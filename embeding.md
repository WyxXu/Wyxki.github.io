# 嵌入文件
> 不要忘記，markdown 是 html 的子集（a very small subset of HTML tags）!

md 内也可插入 \<link> 來引用樣式表，或直接用  \<style> 設置
但既然已有 index.html ，多數情況下還是統一控制為好
（js 脚本同理）

## 圖片
文字鏈接：`[Title](鏈接)`  
插入圖片：`![图片alt](圖源鏈接地址 "图片title")`  
![孫曉艷](2023-01-18_15-53-28.png "孫曉艷")
`![孫曉艷](2023-01-18_15-53-28.png "孫曉艷")`

> 圖片加鏈接：`[![altText](圖源鏈接地址 "title")](點擊链接地址)`

`[filename](media path ':include')`

## 音視頻
* 方法一：使用 html 的 \<video> \<audio> \<iframe> 等標簽
* 方法二：將視頻轉爲 gif，再用 md 語法插入，如：
```markdown
![](https://i0.wp.com/www.printmag.com/wp-content/uploads/2021/02/4cbe8d_f1ed2800a49649848102c68fc5a66e53mv2.gif?fit=476%2C280&ssl=1)
```

![](https://i0.wp.com/www.printmag.com/wp-content/uploads/2021/02/4cbe8d_f1ed2800a49649848102c68fc5a66e53mv2.gif?fit=476%2C280&ssl=1)
* 方法三：用站點的嵌入式外鏈（YouTube、網易雲 等點都提供嵌入式鏈接），如：
```html
<iframe width="560" height="315" src="https://www.youtube.com/embed/ryKT1uIPIaI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
```  
<iframe width="560" height="315" src="https://www.youtube.com/embed/ryKT1uIPIaI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

```html
<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width=330 height=86 src="//music.163.com/outchain/player?type=2&id=1943058854&auto=1&height=66"></iframe>
```

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width=330 height=86 autostart=false src="//music.163.com/outchain/player?type=2&id=1943058854&auto=1&height=66"></iframe>

## PDF
可直接用 html 語法，但多數不能正確顯示，不能實現頁面内查看 PDF     

```html
<object data="透明性.pdf" type="application/pdf" width="100%" height="700px">
    <embed src="透明性.pdf">
        <p>This browser does not support PDFs. Please download the PDF to view it: <a href="透明性.pdf">Download PDF</a>.</p>
    </embed>
</object>
```
或  
```html
<iframe src="透明性.pdf" width="100%" height="700px"></iframe>
```

### PDF.js 
首先到 PDF.js 的 Github 頁面下載最新的 release，解壓到項目文件夾  
然後套用以下代碼  

```html
<iframe src="/pdfjs-3.2.146-dist/web/viewer.html?file=/透明性.pdf" width="100%" height="700px"></iframe>
```
注意 `解壓目錄/web/viewer.html?file=/要查看的pdf文件目錄`  

<iframe src="/pdfjs-3.2.146-dist/web/viewer.html?file=/透明性.pdf" width="100%" height="700px"></iframe>



## Excel
### excel 導出 html
excel 可另存為網頁 —— 然後通過 \<iframe> 嵌入頁面即可  
excel 導出 htm 時一切中文内容包括字體都變成亂碼  
解決方法：`工具-web選項` 編碼選 `utf-8` 并且 `字體` 中 `簡體中文` 字體選 `等綫`

```html
<iframe
     src='xxx.htm'
     width="100%" 
     height="350px"
     frameborder='0'>
</iframe>
```


<iframe
     src='drama.htm'
     width="100%" 
     height="350px"
     frameborder='0'>
</iframe>

<iframe
     src='kouhan.htm'
     width="100%" 
     height="350px"
     frameborder='0'>
</iframe>

iframe 縮放問題，暫時無便捷有效的解決方法  

### excel 轉 md
在 [tableconvert](https://tableconvert.com/) 上可将贴入的 excel 内容  
或 拖入的 excel 文件 转换为 markdown、html、图片 等等等等格式  
复制 入 md 或将 转为图片、html 等再引入 md 便可

类似的在线工具还有 [strerr](https://www.strerr.com/cn/tableizer.html)  將貼入的 excel 内容轉爲 html 表格  
但上述工具的缺點都一樣：丟失跨行跨列格式  

### 搭建在綫表格編輯器

如果是用 angular 等框架建立頁面，可以考慮 用
[Handsontable](https://handsontable.com/docs/7.1.0/frameworks-wrapper-for-react-installation.html) 創建在綫表格

## WORD & PPT

兩條路：  
&#x3000;&#x3000;導出為 pdf 格式，用 PDFjs 顯示  
&#x3000;&#x3000;到處為 html 文件，用 \<iframe> 插入  

<iframe
     src='ros.htm'
     width="100%" 
     height="350px"
     frameborder='0'>
</iframe>