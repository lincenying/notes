
```html
<style>
.half {
    *zoom: expression( this.runtimeStyle['zoom'] = '1', this.innerHTML = '&#x2002;');
}
.full {
    *zoom: expression( this.runtimeStyle['zoom'] = '1', this.innerHTML = '&#x2003;');
}
.half:before { content: '\2002'; speak: none; }
.full:before { content: '\2003'; speak: none; }
</style>

<ul>
    <li class="li">姓<span class="full"></span><span class="full"></span>名：<input type="text" /></li>
    <li class="li">手<span class="half"></span>机<span class="half"></span>号：<input type="text" /></li>
    <li class="li">电子邮箱：<input type="text" /></li>
</ul>
```
