---
layout: post
title: 透過iTerm2 及 oh-my-zsh，打造客製化的終端機
date: 2019-06-20 20:30
categories: [iTerm2, oh-my-zsh]
---

Mac 上預設的終端機大概長得樣子大概都跟下圖差不多，但再看教學影片的時候，總是看到別人的終端機真的很不一樣

![View](https://i.imgur.com/E1819Pi.png)

查了一下發現大家在 Mac 上都很推薦 `iTerm2 + oh-my-zsh`，除了外觀之外，最終要的是`可以分頁`，以後就可以在一個終端機上，開啟終端機分頁

先給大家看結果

![View](https://i.imgur.com/7MkKifx.png)

## Step 1 安裝 Homebrew

Homebrew 是在 Mac 上套件管理的工具，[點我安裝 Homebrew](https://brew.sh/index_zh-tw)

## Step 2 安裝 iTerm2

iTerm2 可以取代 Mac 內建的終端機，使用 Homebrew 下載

```shell
$ brew cask install iterm2
```

## Step 3 iTerm2 主題下載

到[Iterm2-color-schemes](https://iterm2colorschemes.com/)選擇自己喜歡的主題並且下載

## Step 4 開啟 iTerm2 設定主題

於 Launchpad 打開剛剛下載好的 iTerm2
![View](https://i.imgur.com/UWGL49E.png)

左上方 iTerm2 -> Preference -> Profile -> colors

點選 Color Presets 下拉選單，並且匯入下載好的主題(副檔名為.itermcolors)，再點選一次就會出現剛剛下載好的選單主題

![View](https://i.imgur.com/VGOYvj9.png)

## Step 5 安裝 zsh

安裝 zsh 並且將預設終端機改為 zsh，終端機重啟之後就會改變

```shell
$ brew install zsh zsh-completions
$ sudo sh -c "echo $(which zsh) >> /etc/shells"
$ chsh -s $(which zsh)
```

## Step 6 安裝 oh my zsh

oh my zsh 提供了很多 plugin 及 theme 給使用者使用

安裝 oh my zsh

```shell
$ sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

打開 zsh 設定檔，並套用主題

```shell
$ open ~/.zshrc
```

開啟檔案之後，尋找`ZSH_THEME`，將值更改為 agnoster

```
ZSH_THEME="agnoster"
```

若要隱藏當前的用戶名稱及機會名稱可以加上下段

```shell
# optionally set DEFAULT_USER in ~/.zshrc to your regular username to hide the #“user@hostname” info when you’re logged in as yourself on your local machine.
DEFAULT_USER=xxx ## xxx 等於 你的名字
```

## Step 7 修改字體

可以到[Powerline](https://github.com/powerline/fonts)下載喜歡的字體

左上方 iTerm2 -> Preference -> Profile -> text -> change font

## Step 8 安裝 Auto Suggestions

Auto Suggestions 會根據之前輸入的指令推斷要輸入的指令

```shell
$ git clone git://github.com/zsh-users/zsh-autosuggestions $ZSH_CUSTOM/plugins/zsh-autosuggestions
```

加入 plugin

```shell
$ open ~/.zshrc
```

有多個 plugin 以空白隔開，如下

```
plugins=(git zsh-autosuggestions)
```

調整提示訊息的顏色

```
$ open $ZSH_CUSTOM/plugins/zsh-autosuggestions/zsh-autosuggestions.zsh
```

將 fg 調整為 240，提示文字會比較明顯

```
ZSH_AUTOSUGGEST_HIGHLIGHT_STYLE='fg=240'
```

## Step 9 安裝 程式碼高光

安裝`zsh-syntax-highlighting`完後，打開 zsh 設定檔

```shell
$ brew install zsh-syntax-highlighting
$ open ~/.zshrc
```

加入此段

```
# For zsh syntax-highlighting
source /usr/local/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
```

## iTerm2 shortcuts

CMD + T ：新增 tab
CMD + W ：關閉 tab
CMD + R ：清空 command
CMD + Left Arrow ：移置左邊 tab
CMD + Right Arrow ：移置右邊 tab

[iTerm2 shortcuts](https://gist.github.com/squarism/ae3613daf5c01a98ba3a)有提供許多 shortcuts 的 cheat sheet

參考資料：

- [為 MAC 的 Terminal 上色 - 透過 iTerm 2 和 Oh My Zsh 高亮你的終端機](https://pjchender.blogspot.com/2017/02/mac-terminal-iterm-2-oh-my-zsh.html)

- [[心得] iTerm2 + zsh，打造更好的工作環境](http://huli.logdown.com/posts/402147-iterm2-zsh-better-environment)

- [超簡單！十分鐘打造漂亮又好用的 zsh command line 環境](https://medium.com/statementdog-engineering/prettify-your-zsh-command-line-prompt-3ca2acc967f)
