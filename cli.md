# 脚手架指令

## init command
```markdown
docsify init <path> [--local false] [--theme vue] [--plugins false]
```
默認在當前目錄初始化項目，注意：
```
/   文件（磁盤）根目錄
./   同级目錄（當前文件夾，加不加一樣）
../  父級目錄（多加幾個點，就是上溯多少級）
```
主題除 `vue` 外，還可選擇 `bubble`、`dark`、和 `pure`  
`-p` 選項默認 false，為 true 時大概會加載全部可用插件  
（insert as \<script> tags to index.html）

## serve command
```markdown
docsify serve <path> [--open false] [--port 3000]
```
`-o false` 表示禁止 開啓本地服務後 立即用默認瀏覽器打開  
>監聽端口可自選其他

## generate command
```markdown
docsify generate <path> [--sidebar _sidebar.md]
# docsify g <path> [-s _sidebar.md]
```
導航文件的生成不知能否由此類推，未作嘗試