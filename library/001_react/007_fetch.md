# react项目使用fetch
## 使用方法
- `npm install whatwg-fetch --save`
- 在html页面中引入`whatwg-fetch.js`

## 语法
```javascript
// fetch上传文件
var input = document.querySelector('input[type="file"]')

var data = new FormData()
data.append('file', input.files[0])
data.append('user', 'hubot')

fetch('/avatars', {
  method: 'POST',
  body: data
})
// fetch提交表单
var form = document.querySelector('form')

fetch('/users', {
  method: 'POST',
  body: new FormData(form)
})

```

>用fatch发送请求，做session时，不能用res.json()   因为session依赖于cookie，cookie在头信息里设置，res.json()头信息里就没有cookie了


## fetch提交表单
利用ref得到input的dom对象取其value,一旦页面渲染成功就调用ref里的函数，可以操作DOM
```javascript
fetch(url,{
  method:"post",
  headers:{
    contentType::"application/json"
  },
  credentials:"same-origin",
  body:JSON.stringify(data)
})
//获取数据写在生命周期函数中
```
