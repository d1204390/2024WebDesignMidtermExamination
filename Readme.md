# 網頁設計課程期中考作品

## 考題要求
本次期中考要求開發一個奧運獎牌統計網頁，主要考核點包括：
1. 資料處理能力：處理國家獎牌數據和國旗圖片
2. 排序實作：實現多種排序方式
3. 響應式設計：確保在不同設備上正常顯示
4. Bootstrap 應用：使用 Bootstrap 框架進行開發

## 解題思路

### 1. 資料結構設計
將原始的獎牌資料轉換為易於處理的格式：
```javascript
const countryList = medals.map(medal => {
    const [name, gold, silver, bronze] = medal.split(' ');
    return {
        name: name.replace(/-/g, ' '),
        gold: parseInt(gold),
        silver: parseInt(silver),
        bronze: parseInt(bronze),
        total: parseInt(gold) + parseInt(silver) + parseInt(bronze)
    };
});
```

### 2. 視覺呈現
使用 Bootstrap 卡片元件來展示每個國家的資料：
```html
<div class="country-card col-lg-2 col-md-3 col-sm-4 col-6">
    <div class="card-body">
        <h5 class="card-title">${country.name}</h5>
        <img src="img/${country.name.toLowerCase()}.png" class="card-img-top">
        <div class="medals mt-2">
            <span class="medal gold">${country.gold}</span>
            <span class="medal silver">${country.silver}</span>
            <span class="medal bronze">${country.bronze}</span>
        </div>
    </div>
</div>
```

### 3. 排序功能實作
實現了三種排序方式：
```javascript
// 按國家名稱排序
function sortByName() {
    const sorted = [...countryList].sort((a, b) => a.name.localeCompare(b.name));
    renderTable(sorted);
}

// 按金牌數量排序
function sortByGold() {
    const sorted = [...countryList].sort((a, b) => b.gold - a.gold);
    renderTable(sorted);
}

// 按總獎牌數排序
function sortByTotal() {
    const sorted = [...countryList].sort((a, b) => b.total - a.total);
    renderTable(sorted);
}
```

## 使用的技術
1. **HTML5/CSS3**
    - 語意化標籤
    - Flexbox 布局
    - 媒體查詢

2. **JavaScript**
    - ES6+ 語法
    - 陣列處理
    - DOM 操作

3. **Bootstrap 5.3.3**
    - 響應式網格系統
    - 輪播元件
    - 按鈕樣式

## 學習收穫

### 1. JavaScript 技能
- 學會使用 ES6 解構賦值
- 掌握陣列排序方法
- 理解 DOM 操作技巧

### 2. Bootstrap 應用
- 熟悉網格系統使用
- 學會運用 Bootstrap 元件
- 理解響應式設計原理

### 3. 網頁開發能力
- 提升 CSS 布局技巧
- 加強程式碼組織能力
- 理解資料處理流程

## 心得體會
通過這次期中考，我：
1. 更熟練地運用了 Bootstrap 框架
2. 加深了對 JavaScript 的理解
3. 提升了網頁開發的實作能力
4. 學會了如何組織和處理複雜的資料

## 改進空間
1. 可以添加更多互動效果
2. 優化載入效能
3. 增加資料過濾功能
4. 改善行動裝置的使用體驗

這次期中考讓我對網頁開發有了更深入的理解，也幫助我發現了需要加強的領域。我會繼續努力學習，提升自己的技術能力。