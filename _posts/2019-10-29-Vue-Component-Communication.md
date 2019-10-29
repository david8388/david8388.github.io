---
layout: post
title: Vue Component(元件) 互相溝通
date: 2019-10-29 21:45
categories: [Vue]
---

## Component 資料如何互相溝通

在父元件(Header.vue)中使用子元件(Card.vue)

如下圖紅色方框處，即為 Child Component

![pic](https://i.imgur.com/93TBy79.png)

首先看父元件(Header.vue)的程式碼

```html
<template>
  <div>
    <label for="name">Name</label>
    <input type="text" v-model="name" />
    <label for="jobTitle">Job Title</label>
    <input type="text" v-model="jobTitle" />
    <card :name="name" :jobTitle="jobTitle" />
    <h1>{{ msg }}</h1>
  </div>
</template>

<script>
  import Card from "@/components/Card";

  export default {
    name: "HelloWorld",
    components: {
      Card
    },
    data() {
      return {
        name: "David Wu",
        jobTitle: "Software Engineer",
        msg: "Welcome to Your Vue.js App"
      };
    }
  };
</script>
```

父元件中，透過 v-model 實現雙向綁定，輸入框的資料若有異動，則會異動到子元件相對的屬性

子元件(Card.vue)程式碼如下

```html
<template>
  <div>
    <div>
      <i class="fas fa-user-tie fa-10x"></i>
      {% raw %}
      <h4><b>{{ name }}</b></h4>
      {% endraw %} {% raw %}
      <p>{{ jobTitle }}</p>
      {% endraw %} {% raw %}
      <h4><b>{{ name }}</b></h4>
      {% endraw %}
    </div>
  </div>
</template>

<script>
  export default {
    name: "Card",
    props: {
      name: {
        type: String,
        default() {
          return "";
        }
      },
      jobTitle: {
        type: String,
        default() {
          return "";
        }
      }
    }
  };
</script>
```

現在需要異動子元件的資料，所以`在子元件新增兩個 Button 透過 methods 來異動props`

```html
<template>
  <div>
    <div>
      <i class="fas fa-user-tie fa-10x"></i>
      {% raw %}
      <h4><b>{{ name }}</b></h4>
      {% endraw %} {% raw %}
      <p>{{ jobTitle }}</p>
      {% endraw %}
      <button @click="changeName">Change Name</button>
      <button @click="changeTitle">Change Title</button>
    </div>
  </div>
</template>

<script>
  export default {
    name: "Card",
    ...
    methods: {
      changeName: function() {
        this.name = "Joe Doe";
      },
      changeTitle: function() {
        this.jobTitle = "Sales";
      }
    }
  };
</script>
```

![pic](https://i.imgur.com/Fr3uElV.png)

看到上圖可以知道，父元件的資料沒有跟著改變，打開 F12 發現下面得錯誤訊息

```
[Vue warn]: Avoid mutating a prop directly since the value will be overwritten
whenever the parent component re-renders. Instead, use a data or computed
property based on the prop's value. Prop being mutated: "name"
```

問題是在於`prop是單向綁定，父組件屬性發生變化，會傳給子元件; 但相反的子元件屬性改變，並不會跟著改變父元件的屬性`，是為了防止子元件無意間修改了父組件的狀態，會讓數據流難以理解

首先要在子元件中將各個 props 用副本先儲存起來

舉例來說：再 data`新增 myName 就將預設值設為name` 這個 prop，再 `changeName 的時候，新增一段this.$emit("nameChanged", this.myName);`

```html
<template>
  <div>
    <div>
      <i class="fas fa-user-tie fa-10x"></i>
      {% raw %}
      <h4><b>{{ name }}</b></h4>
      {% endraw %} {% raw %}
      <p>{{ jobTitle }}</p>
      {% endraw %}
      <button @click="changeName">Change Name</button>
      <button @click="changeTitle">Change Title</button>
    </div>
  </div>
</template>

<script>
  export default {
    name: "Card",
    props: {
      name: {
        type: String,
        default() {
          return "";
        }
      },
      jobTitle: {
        type: String,
        default() {
          return "";
        }
      }
    },
    data() {
      return {
        myName: this.name
      };
    },
    methods: {
      changeName: function() {
        this.myName = "Joe Doe";
        this.$emit("nameChanged", this.myName);
      },
      changeTitle: function() {
        this.jobTitle = "Sales";
      }
    }
  };
</script>
```

子元件會發射`nameChanged這個 event`，所以在父元件需要新增這個 method

`再 card 元件中 新增 @nameChanged="onNameChanged"`，@nameChanged 即對應到子元件發射的 eventName

```html
<template>
  <div>
    ...
    <card :name="name" :jobTitle="jobTitle" @nameChanged="onNameChanged" />
    ...
  </div>
</template>

<script>
  import Card from "@/components/Card";

  export default {
    name: "HelloWorld",
    components: {
      Card
    },
    data() {
      return {
        name: "David Wu",
        jobTitle: "Software Engineer",
        msg: "Welcome to Your Vue.js App"
      };
    },
    methods: {
      onNameChanged: function(newVal) {
        this.name = newVal;
      }
    }
  };
</script>
```

如此一來子元件調整後的屬性值，也會更新到父元件對應的屬性

![pic](https://i.imgur.com/ss3JHk3.png)

參考資料：

- [如何在 Vue2 中实现组件 props 双向绑定](https://juejin.im/entry/5843abb1a22b9d007a97854c)

- [Vue.js 2.0 Components Communication](https://medium.com/@guitarbien/vue-js-2-0-components-communication-84e0c4598b82)
