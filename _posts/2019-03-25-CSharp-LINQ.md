---
layout: post
title: C# LINQ
date: 2019-03-25 20:20
categories: [Dotnet, CSharp, LINQ]
---

LINQ(Language-Integrated Query)，是.NET Framework 3.5 開始新增的語言功能
特色是`具備資料查詢的能力`，語法就`像是 SQL 的語法`

### 查詢作業需要三個部分

1. 取得資料來源
2. 建立查詢
3. 執行查詢

範例說明

```csharp
class Person {
    public string Name { get; set; }
    public string Gender { get; set; }
}

public static void Main () {
    // 1. 資料來源
    List<Person> person = new List<Person> {
        new Person { Name = "Shawn", Gender = "Male" },
        new Person { Name = "Erin", Gender = "Female" },
        new Person { Name = "David", Gender = "Male" },
        new Person { Name = "Susan", Gender = "Female" },
        new Person { Name = "Joe", Gender = "Male" },
        new Person { Name = "Eric", Gender = "Male" }
    };

    // 2. 建立查詢
    var result = from p in person
            	where p.Gender == "Female"
            	select p;

    // 3. 執行查詢
    foreach (var r in result) {
        Console.WriteLine ("Name is {0}, Gender is {1}", r.Name, r.Gender);
    }
}
```

```
output
Name is Erin, Gender is Female
Name is Susan, Gender is Female
```

- from ... in ： 指定資料來源
- where： 條件式判斷，套用篩選
- select ：取得查詢物件

另提取資料語法中有一個`select new`，可以依照所設定的屬性產生類別物件，這個語法包含兩個功能：物件初始值 及 匿名型別

```csharp
class Person {
    public string Name { get; set; }
    public string Gender { get; set; }
}

public static void Main () {
    List<Person> person = new List<Person> {
        new Person { Name = "Shawn", Gender = "Male" },
        new Person { Name = "Erin", Gender = "Female" },
        new Person { Name = "David", Gender = "Male" },
        new Person { Name = "Susan", Gender = "Female" },
        new Person { Name = "Joe", Gender = "Male" },
        new Person { Name = "Eric", Gender = "Male" }
    };

    var result = from p in person
            	where p.Gender == "Female"
            	select new {
			name = p.Name,
			gender = p.Gender,
			age = 18
		};

    foreach (var r in result) {
        Console.WriteLine("Name {0}, Gender {1}, Age {2}", r.name, r.gender, r.age);
    }
}
```

```
output
Name David, Gender Male, Age 20
Name Eric, Gender Male, Age 20
Name Joe, Gender Male, Age 20
Name Shawn, Gender Male, Age 20
```

LINQ 依照使用對象可以區分為

1. [LINQ to Objects](https://docs.microsoft.com/zh-tw/dotnet/csharp/programming-guide/concepts/linq/linq-to-objects)
2. [LINQ to XML](https://docs.microsoft.com/zh-tw/dotnet/csharp/programming-guide/concepts/linq/linq-to-xml)
3. [LINQ to DataSet](https://docs.microsoft.com/zh-tw/dotnet/framework/data/adonet/linq-to-dataset)
4. [LINQ to SQL](https://docs.microsoft.com/zh-tw/dotnet/framework/data/adonet/sql/linq/index)

參考資料：

- [LINQ 簡介](https://docs.microsoft.com/zh-tw/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq)
- [LINQ 寫法：類 SQL 查詢語法 vs 方法串接](https://blog.darkthread.net/blog/linq-sql-query-vs-methods/)
