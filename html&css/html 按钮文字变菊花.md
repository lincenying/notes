
```html
<style>
.button {
    display: inline-block;
    line-height: 38px; min-width:46px;
    padding:0 16px;
    border:1px solid #D0D0D5; border-radius:4px;
    background: #fff center;
    font-size: 14px; text-align: center; color:#333;
    -webkit-transition: all .2s; transition: all .2s;
    cursor: pointer;
}
.button:hover {
    text-decoration: none;
    border-color: #c0cdc5;
}
.loading {
    color: transparent;
    border-color: #c0cdc5;
    background: #f0f0f0 url(../image/loading_s.gif) no-repeat center;
    cursor: default;
    pointer-events: none;
}
</style>

<a href="javascript:" id="button" class="button">按钮</a>

<script>
var button = document.getElementById("button");
if (button) {
    button.onclick = function() {
        var className = this.className;
        if (/loading/.test(className) == false) {
            button.className += " loading";
            setTimeout(function() {
                button.className = "button";
            }, 2000);
        }
    };
}
</script>
```
