# Answer
## 請用兩種 css 方法排出以下版面
### 1. css layout version 1
```
// CSS
.wrapper {
  height: 100vh;
}
.top {
  height: 30px;
}
.bottom {
  height: 30px;
}
.middle {
  display: flex;
  height: calc(100% - 60px);
}
.middle > .side {
  width: 60px;
}
.middle > .main {}

// HTML
<div class="wrapper">
  <div class="top"></div>
  <div class="middle">
    <div class="side"></div>
    <div class="main"></div>
  </div>
  <div class="bottom"></div>
</div>
```


### 2. css layout version 2
```
// CSS
.wrapper {
  display: grid;
  height: 100vh;
  grid-template-columns: 60px calc(100% - 60px);
  grid-template-rows: 30px calc(100% - 60px) 30px;
}
.top {
  grid-row: 1;
  grid-column: 1 / -1;
}
.side {
  grid-row: 2;
  grid-column: 1;
}
.main {
  grid-row: 2;
  grid-column: 2;
}
.bottom {
  grid-row: 3;
  grid-column: 1 / -1;
}

// HTML
<div class="wrapper">
  <div class="top"></div>
  <div class="side"></div>
  <div class="main"></div>
  <div class="bottom"></div>
</div>
```

---
## 使用 React Hook 完成,按住 Shift 可多選清單 Checkboxes ( 其中有不可選的須跳過 )
### Answer: [Link](https://github.com/GlennJong/section-list)

拆分成 `Item` 和 `List` 兩個元件：<br />
`Item` 僅負責自身的 checkbox state。<br />
`List` 負責選取邏輯，選取時透過 ref 存取 checkbox 狀態，避免使用 state 造成不必要的 life cycle。

---
## 請概述通常前端 CRUD 會用到的後端 API 有哪些，規格是甚麼？
### Answer:
### 前端透過 API 進行與後端的程式溝通，CRUD 是代表 Create、Read、Update、Delete 這四個動作，向指定的 api url 發送 request，使後端進行相對應的資料處理動作。<br />
### 為了有更好的維護性與效能進行最佳化處理，例如使用 RESTful 風格會將 request method 做成更語義化的請求分類：<br />
Create：POST<br />
Read：GET<br />
Update：PUT<br />
Delete：DELETE<br />
### 後端開 API 規格文件大致會分成：
url: api 的位址，也可以透過 params 的方式傳值給後端。<br />
request method: 使用 POST、GET、PUT、DELETE 哪一種方式進行請求。<br />
request header: 存放資料與設定的字串，例如設置 token 驗證請求的可行性。<br />
request body: 可存放的內容更多，例如 formData。<br />
response: 送出請求後，後端完成動作後再回傳的內容，例如動作結果的狀態或描述 `{ status: 'error' }` 之類的內容。<br />
