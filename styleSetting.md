# 樣式美化
> md 一定程度上兼容 html，可借内置 \<style> 或 tag 内聯樣式實現

## 主題色
`themeColor: '#colorHex'` 只影響部分文字和元素顔色  
要修改全局主題，替換 index.html 中的 \<link> 
```html
  <!-- 官方主題 -->
  <link rel="stylesheet" href="//unpkg.com/docsify/themes/vue.css">
  <link rel="stylesheet" href="//unpkg.com/docsify/themes/buble.css">
  <link rel="stylesheet" href="//unpkg.com/docsify/themes/dark.css">
  <link rel="stylesheet" href="//unpkg.com/docsify/themes/pure.css">
  <link rel="stylesheet" href="//unpkg.com/docsify/themes/dolphin.css">
```
## 自定義樣式
* 方法一：從官方主題的 \<link> 中獲取樣式文件，保存下來，改一套自己的模板
  * 可以搜索其他來源的 markdown 樣式
* 方法二：少部分改動可在 index.html 中使用 \<style> 標簽設置

```CSS
/* 善用 開發者工具 找出 對應的 選擇器 */
.anchor span { /* 這是控制所有標題樣式的選擇器 */ }
```