# 各頁面功能介紹

## HomeView.vue
1. 設定三個按鈕對應到 text, radio, select
2. 設置一個 computed 變數 inputType，當按下按鈕時，根據按鈕類型將不同字串賦值給 inputType（例如：按下 input text 按鈕，則將 text 賦值給 inputType）
3. inputType 用 setter 接收傳進來的變數，再賦值給 this.type，其中，this.type 預設值為 'text'，表示畫面一載入時，預設顯示 <input type="text">
4. 將 inputType 透過 props 傳入 inputComponent.vue
5. 設置一個 receiveOutput 方法接收 inputComponent.vue 傳來的變數，並設置 output 變數接收，再將 output 透過 props 傳入 outputComponent.vue
6. 設置 toggleTheme 方法動態新增 class=dark，切換頁面主題顏色。

## inputComponent.vue
1. 根據傳入的 inputType，搭配 v-if，有條件地呈現元件。例如：v-if="inputType === 'text'" 則呈現 <input type="text">
2. 設置 output 變數綁定 v-modal 呈現結果，不論是 <input> 或 <select> 都共用此變數。
3. 用 watch 監聽 inputType，當 inputType 有變動時（即點選不同按鈕時）， 將 output 內容清空。
4. 用 watch 監聽 output，當 output 有變動時，將 output $emit 給父元件 HomeView.vue。

## outputComponent.vue
1. 接收 inputComponent.vue 傳入的 props 並呈現在畫面上。

## main.scss
1. 第 2-10 行定義預設樣式的變數，第 22-26 行則為 dark mode 的變數，於 main.js import

# 想法
1. 將三種 input 放在同一個 component 統一管理，output 則是用另一個 component，以後有類似呈現 output 需求皆可透過 props 呈現
2. 將主題顏色分區管理，將來如有其他 theme mode 的需求，皆可仿照 dark 的方式
