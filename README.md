# myvim
我的vim配置，目前主要是针对golang开发，需要vim8.1以上的版本。

## 安装

### 准备
使用了coc.nvim插件作为补全客户端，coc依赖nodejs和yarn，所以先安装这2者。<br>
+ nodejs
```
https://nodejs.org/zh-cn/download/
```

+ yarn
```
https://yarnpkg.com/lang/en/
```
+ ripgrep
windows下可以用bin/win/rg.exe，mac和Linux请参照
```
https://github.com/BurntSushi/ripgrep
```
+ universal-ctags
使用Universal-ctags代替exuberant-ctags，因为后者多年没有更新了
```
https://github.com/universal-ctags/ctags
```

### 启动
安装好vim后，将vim文件夹拷贝到安装目录。
win下拷贝到vimfiles，mac和linux放到用户目录的.vim文件夹。<br>
1. 安装插件
```
:PlugInstall
```
2. Coc配置
```
 装完coc后需要配置gopls作为lsp server
 :CocConfig
{
  "languageserver": {
    "golang": {
      "command": "gopls",
      "args":[],
      "rootPatterns": ["go.mod", ".vscode"],
      "filetypes": ["go"],
      "initializationOptions": {
        "usePlaceholders": true,
        "buildFlags":["-tags=NEW_APP NEW_WEB"]
      }
    }
  },
  "suggest.maxPreviewWidth": 200,
  "coc.preferences.extensionUpdateCheck": "weekly"
}

安装gopls等工具，指定proxy:
env http_proxy=socks5://127.0.0.1:1081 https_proxy=socks5://127.0.0.1:1081 vim -c 'GoInstallBinaries' -c qa

 安装coc-list
 :CocInstall coc-lists
 coc-list操作界面的key map，见:h coc-list-mappings

 安装coc-json, 提供配置补全
 :CocInstall coc-json

 遇到问题，可以重启coc服务
 :CocRestart
```
### python
使用coc-pyright
```
:CocInstall coc-pyright

```

### help
doc文件夹里已经带了myvim的一些笔记，用下面的命令可以查看:
```
:h myvim
```
