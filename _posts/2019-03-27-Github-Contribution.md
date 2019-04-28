---
layout: post
title: Github 為什麼沒有紀錄 contributions
date: 2019-03-26 22:25
categories: [Github, Git]
---

到目前為止也已經寫了 3 篇文章，但是發現到了我的 `Github 上的contribution graph 似乎跟Commit次數不成對比`
就看了一下 Github 如何計算 contribution

### Issues and pull requests

- 必須是獨立的 repo，不能是 fork

### Commits

- `commits 使用的 email 帳號必須和 Github 帳號有關`
- 必須是獨立的 repo，不能是 fork
- commits 必須是在
  - repo 的預設分支上（`通常是 master`）
  - 在 gh-pages 分支(包含 Project Pages sites 的 repo)

### 必須滿足下列至少一個條件

- repo 上的共同協作者 或是 擁有該 repo 組織的一員
- 已經 fork 過該 repo
- 對此 repo 發起 PR or Issue
- 對此 repo 給過星星

### 常見問題

- 可能是 Github 延遲的問題（當 24 小時候後，再看一次）
- `本地 git email 與 Github 帳號的email 沒有關聯`
- commits 必須是在 repo 的預設分支上或是在 gh-pages 分支
- commits 在 fork 上會無法紀錄 contribution

看到我標紅色的那點了嗎？ 其實我的問題點就在這

### 查看 Commit 紀錄

下`git log`查看紀錄，`email 的資料跟 Github 上所設定的資料不同`
![查看紀錄](https://i.imgur.com/feSRub6.png)

commit 的相關資料並沒有設定好，需要調整一下本地端 git 的相關資料

```
git config --global user.email "email帳號"
git config --global user.name "名稱"
```

調整完後再執行 commit，Github 上的 contribution graph 也成功紀錄此次的 commit
![結果](https://i.imgur.com/5FAo7MG.png)

參考資料：

- [为什么 Github 没有记录你的 Contributions](https://segmentfault.com/a/1190000004318632)
- [Why are my contributions not showing up on my profile?](https://help.github.com/en/articles/why-are-my-contributions-not-showing-up-on-my-profile)
