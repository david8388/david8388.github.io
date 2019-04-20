---
title: Phabricator 工作流程
date: 2019-04-13 10:10
categories: [Phabricator, Git]
---

最近工作上的需要, 存放代碼的平台從 Azure DevOps 轉換成 Phabricator

第一次接觸覺得`最大的差別就是 Code Review`, 工作上`需要指定Reviewer`, `Reviewer看完 approval 之後才能上 Phabricator`

## Configuration
首先在Phabricator官網註冊試用版的
![註冊](https://i.imgur.com/MyXeXCy.png)

選擇試用版（只有7天有效期限, 到期後會自動刪除專案）
![選擇](https://i.imgur.com/myq4W4B.png)

驗證完後, 會導入到主畫面
![畫面](https://i.imgur.com/Fp2Ti4u.png)

主畫面左邊點選Diffusion 
![畫面](https://i.imgur.com/xvjm0ey.png)

點選 + create repository 
![畫面](https://i.imgur.com/XzjTNIl.png)

選擇Git
![畫面](https://i.imgur.com/b6LE0IU.png)

命名後 並啟動repo
![畫面](https://i.imgur.com/wGNg5Ep.png)
![畫面](https://i.imgur.com/J36dawQ.png)

記得再設置檔添加SSH Key, 不然待會clone會有問題
![畫面](https://i.imgur.com/8t4ZIdM.png)

回到Diffusion畫面, 點選剛剛所創建的repo, 接著點擊旁邊的clone 複製代碼
![畫面](https://i.imgur.com/tQtMvPx.png)

移置clone後的專案路徑, 並新增README

```bash
cd ~/SideProject/phabricator-test
echo "Hello, phabricator test">> README.md
git add .
git status (確認 REAMDME 是否有加入)
git commit -m 'init commit'
```

接著下 `arc diff`
會有所需要填寫的資料
- Reviewers   改的code要請誰幫你做code review
- Subscribers 改的code要讓專案中的哪些人知道 

![畫面](https://i.imgur.com/enWGxJW.png)

畫面中可以看到增加或修改什麼檔案
![畫面](https://i.imgur.com/vdDa47P.png)

另外配置Phabricator的URI
```
arc set-config default https://test-tppr25itewwg.phacility.com/
```

再要push到Phabricator的專案中 加入.arcconfig
```
{
  "phabricator.uri": "https://test-tppr25itewwg.phacility.com/"
}
```

下達git 
```bash
git add .
git status (確認 REAMDME 是否有加入)
git commit  -m 'add arcconfig'
arc diff (reviewers approval後就可以往下執行)
arc land
```

參考資料：

- [Phabricator 個人備忘](https://medium.com/@fcamel/phabricator-%E5%80%8B%E4%BA%BA%E5%82%99%E5%BF%98-e04da1202c59)
- [How to Install PHP 7 on MacOS](https://tecadmin.net/install-php-macos/)
- [Arcanist Quick Start](https://secure.phabricator.com/book/phabricator/article/arcanist_quick_start/)
- [OSX Arcanist Installation Guide](https://gist.github.com/potench/68d48757d0d56842946a)
- [How to solve Permission denied (publickey) error when using Git?](https://stackoverflow.com/questions/2643502/how-to-solve-permission-denied-publickey-error-when-using-git)