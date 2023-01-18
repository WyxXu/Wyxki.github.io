


# 文檔系統搭建
> 用途：内部 Wiki、個人博客


## 基礎環境設置
` npm i docsify-cli -g ` 安裝脚手架  
` mkdir my-docs ` or ` mkdir [-p] dirName` 創建目錄  
（後一寫法是檢查目錄是否已存在，不存在才創建）  
` cd my-docs ` 轉到目錄文件夾
> 單獨創建一個文件夾存放項目，再在該文件夾創建環境  
這裏常見的錯誤是 cmd 中操作時 docsify 少輸入個 s

## 項目初始化
`docsify init ./folderNm` 創建項目文件夾  

項目文件夾創建後會自動生成三個文件。 其中：  
`README.md` 作爲主页内容渲染；  
`index.html` 是入口文件，配置用；   
`.nojekyll` 用於防止解析時忽略掉下劃綫開頭的文件  

## 本地預覽
`docsify serve folderNm` 啓動本地服務器  
瀏覽器輸入 `127.0.0.1:3000` 或 `http://localhost:3000` 可見  
任何改動一保存即使更新  
若接口已占用，或出於其它原因不想使用默認接口，可  
`docsify serve docs --port portNo` 自定義

## index.html 配置詳解
>該文件的内容決定所有 md 文件如何渲染為 html 頁面  
因此字符編碼、http請求、頁面適配等都在其中設置

```html
<div id="main">林北正在給你加載中</div>
<script>
      window.$docsify = {
        name: '',
        repo: '',
        loadSidebar: true,
        subMaxLevel: 2
}
  </script>
```
### 非視覺配置
#### 渲染挂載
` READ.md ` 解析為 html 後都挂在到 id 為 main 的元素上渲染  
可在  `window.$docisify` 中添加 `el: '#blahblah'` 修改  
`<div id="main">` 需對應改爲 `<div data-app id="blahblah">` 
el 參數的值是一個 css 選擇器， 默認值是 #app，  
如果 #app 不存在，就綁定到 body 上  

#### 路徑設置
`basePath` 設置文檔加載的根路徑  
可以渲染 其他域名的文檔 或 GitHub 倉庫
`relativePath` 布爾值，爲真時鏈接使用相對路徑，默認 false

#### 路由設置
routerMode

### 視覺設置

#### 首頁切換
若不想用 READ.md 作首頁文件，或寫有幾個首頁文件備用，  
用 `homePage: 'xx.md'` 切換首頁加載路徑 

#### 封面頁
Set `coverpage` to true, and create a `_coverpage.md`  
若自定義文件名，需要再添加參數 `coverpage: 'cover.md'`  
>A document site can have only one coverpage!

#### 側邊欄設置（TOC）
`name` 是側邊欄的標題，可用 `nameLink: '/'` 添加鏈接  
`logo: '/'` 用 icon 來代替側邊欄的文字標題，↑鏈接仍然有效  
icon 的大小可用 css 調節，如何控制 md 内容樣式另文詳述 

側邊欄是文檔目錄的容器，默認從 READ.md 的標題層級 自動創建
`maxLevel: 'n'` 讀取 md 文件目錄的層級（最大值 6）   

當存在頁面嵌套時，就需要外部文件來定義TOC  
`loadSidebar: true` ，即從 `_sidebar.md` 讀取側邊欄内容  
相應地，讀取外部文件目錄的層級參數是 `subMaxLevel: 'n'`   
`autoHeader: true`，根據  `_sidebar.md` 内容自動生成頁面名  

若文檔不需要目錄或特殊原因不便顯示，加 `hideSidebar: true`  

#### 導航欄設置
添加 `loadNavbar: true` ，就會從 _navbar.md 加載導航欄内容
導航欄貫穿全部頁面（無論什麽層級的頁面都會在頂部顯示）  
`mergeNavbar: true` 小屏環境下自動將導航欄合并到側邊欄

#### topMargin
點擊頁面二級標題後，會跳至標題処，且標題上滾至頁面頂部  
此參數接受整數值，使標題上滾後距離頁面頂部還保持一定距離  

#### GitHub 挂件
`repo: username/repo` 添加 GitHub 頁面鏈接後面右上角會出現 GitHub 挂件，
點擊挂件跳轉到指定 GitHub 頁


### 脚本及動效
`executeScript: true;` 允許頁面執行自定義脚本  
會執行 md 文件中第一個 script 標簽
外鏈脚本（src=''）要搭配以下插件：
```html
<script 
    src="
    //cdn.jsdelivr.net/npm/docsify/lib/plugins/external-script.min.js
    ">
</script>
```
所有頁面所需脚本都可以在 index.html 中分別載入

#### 頁面切換後跳至頁面頂部
`auto2top: true`  
>Scrolls to the top of the screen when the route is changed.

### 其它
#### 時間戳
`formatUpdated: '{ MM} /{ DD}  { HH} :{ mm} ',`

#### 字數統計 

```html
<!-- 添加參數 -->
count: {
    countable: true,
    fontsize: '0.9em',
    color: 'rgb(90,90,90)',
    language: 'chinese'
}
<!-- 加入插件 -->
<script src="//unpkg.com/docsify-count/dist/countable.js"></script>
```

#### 全局搜索
```html
<!-- 參數設置 -->
search: {
    paths: 'auto',
    placeholder: '全局搜索關鍵詞',
    noData: '尋毋到哦',
    depth: 6,
},
<!-- 加入插件 -->
<script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/search.min.js"></script>
```
#### 快捷複製
在代碼塊右上角加一鍵複製到剪貼板按鈕
```html
<!-- 加入插件 -->
<script src="//cdn.jsdelivr.net/npm/docsify-copy-code"></script>
```