多行文字垂直居中:

```html
<style>
    .align_box_2 {
        display: table-cell;
        width: 550px;
        height: 1.14em;
        padding: 0 0.1em;
        border: 4px solid #beceeb;
        color: #069;
        font-size: 10em;
        vertical-align: middle;
    }

    .align_box_2 span.align_word {
        display: inline-block;
        font-size: 0.1em;
        vertical-align: middle;
    }
</style>
<div class="align_box_2"><span class="align_word">这里显示多行文字。</span></div>
```

图片的垂直居中:

```html
<ul class="align_box_3 fix">
    <li>
        <img src="../image/pixel.gif" style="background-image:url(image/study/s/s128/mm1.jpg);" />
    </li>
</ul>
<style>
    .align_box_3 li {
        width: 1em;
        height: 1em;
        padding: 0.1em;
        margin: 0 0.1em 0 0;
        font-size: 128px;
        float: left;
        border: 1px solid #beceeb;
    }

    .align_box_3 li img {
        display: block;
        width: 100%;
        height: 100%;
        background-repeat: no-repeat;
        background-position: center;
    }
</style>
```

图片的垂直居中:

```html
<ul class="align_box_4 fix">
    <li>
        <div><img src="image/study/s/s128/mm1.jpg" /></div>
    </li>
</ul>
<style>
    .align_box_4 li {
        float: left;
        margin-right: 13px;
    }

    .align_box_4 li div {
        display: table-cell;
        width: 144px;
        height: 144px;
        border: 1px solid #beceeb;
        font-size: 118px;
        text-align: center;
        vertical-align: middle;
    }

    .align_box_4 li div img {
        vertical-align: middle;
    }
</style>
```

图片的垂直居中:

```html
<div class="align_box_5 fix">
    <a href="#zhangxinxu">
        <img src="image/study/s/s128/mm1.jpg" />
    </a>
    <a href="#zhangxinxu">
        <img src="image/study/s/s128/mm2.jpg" />
    </a>
</div>
<style>
    .align_box_5 a {
        display: inline-block;
        width: 1.2em;
        font-size: 128px;
        text-align: center;
        vertical-align: middle;
    }

    .align_box_5 a img {
        vertical-align: middle;
        padding: 2px;
        border: 1px solid #beceeb;
    }
</style>
```

图片的垂直居中:

```html
<ul class="align_box_6 fix">
    <li>
        <img class="show_img" src="image/study/s/s128/mm1.jpg" />
        <img class="alpha_img" src="../image/pixel.gif" />
    </li>
</ul>
<style>
    .align_box_6 li {
        height: 128px;
        width: 150px;
        padding: 13px 0;
        float: left;
        margin-right: 10px;
        border: 1px solid #beceeb;
        text-align: center;
        font-size: 0;
    }

    .align_box_6 li .alpha_img {
        height: 100%;
        width: 1px;
        vertical-align: middle;
    }

    .align_box_6 li .show_img {
        vertical-align: middle;
    }
</style>
```

图片的垂直居中:

```html
<style>
    .ul_image {
        overflow: hidden;
        zoom: 1;
    }

    .ul_image li {
        float: left;
        width: 150px;
        height: 150px;
        text-align: center;
        line-height: 150px;
        *font-size: 125px;
    }

    .ul_image li:after {
        content: ' ';
        vertical-align: middle;
    }

    .ul_image li img {
        vertical-align: middle;
    }
</style>
<ul class="ul_image">
    <li><img src="image/study/s/s128/mm1.jpg" /></li>
    <li><img src="image/study/s/s128/mm2.jpg" /></li>
    <li><img src="image/study/s/s128/mm3.jpg" /></li>
    <li><img src="image/study/s/s128/mm4.jpg" /></li>
    <li><img src="image/study/s/s128/mm5.jpg" /></li>
    <li><img src="image/study/s/s128/mm6.jpg" /></li>
</ul>
```
