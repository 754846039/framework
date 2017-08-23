#　富文本编辑器(高度传入)

- 下载npm install wangeditor     
- 拷贝css-->public/css
- 拷贝fonts
- 拷贝两个js  wangEditor.js和jquery.js
- 在html引入js、css（前后台都需要引入css）
```html
<div id="div1">
    <p>请输入内容...</p>
</div>
<script type="text/javascript">
    var editor = new wangEditor('div1');
    editor.create();
</script>
```
