```css
/*  去除点击时的阴影
    none：
    文本不能被选择
    text：
    可以选择文本
    all：
    当所有内容作为一个整体时可以被选择。
    element：
    可以选择文本，但选择范围受元素边界的约束
 */
a {
    -webkit-tap-highlight-color:rgba(255,255,255,0);
}

/*  文本不能被选择
    auto： 使用默认的拖拽行为，这种情况只有图片和链接可以被拖拽。
    element： 整个元素而非它的内容可拖拽。
    none： 元素不能被拖动。在通过选中后可拖拽。
 */
.div {
    -webkit-user-select:none;
}

/* 禁用拖动效果 */
.div {
    -webkit-user-drag: none;
}

/* 快速滚动和回弹: */
.div {
    -webkit-overflow-scrolling : touch;
}

/* 禁止按钮使用原生按钮样式: */
button, input {
    -webkit-appearance : none;
}
```

```html
/* 适应宽度，禁止缩放 */
<meta name="viewport" content="initial-scale=1, maximum-scale=1, minimum-scale=1, width=device-width, user-scalable=no">

/* 防止被百度抓取转码 */
<meta http-equiv="Cache-Control" content="no-transform">
<meta http-equiv="Cache-Control" content="no-siteapp">
```
