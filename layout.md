# 自定義導航欄
> 使用 Docsify + Markdown語法； 用途：内部 Wiki

## html 方法
可用 html 在 md 内部創建，注意鏈接都要用 `#/` 開頭

```html
<body>
  <nav>
    <a href="#/">EN</a>
    <a href="#/zh-cn/">中文</a>
  </nav>
  <div id="app"></div>
</body>
```
或用另一個 md 文件（_navbar.md）創建導航内容  

## markdown 方法
```markdown
* [En](xx.md)
* [简体中文](xx.md)
```

如果導航内容過多，可做成下拉列表式

```markdown
* 頂層顯示
  * [下拉選項1](xx.md)
  * [下拉選項2](xx.md)
  * [下拉選項3](xx.md)
  * [下拉選項4](xx.md)  
```

搭配 emoji 插件，
```HTML
<script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/emoji.min.js"></script>
```
即可使用 國旗 等 emoji 作導航鏈接的 icon  
（語法`:emojistring:`，如 `[:100:](/)` 顯示為 [:100:](/)）
```markdown
* [:us:, :uk:](/)
* [:cn:](/)
```
