# 属性和方法
>1. [计算属性](#计算属性 "计算属性")
1. [methods](#methods "methods")
1. [watch](#watch "watch")
1. [生命周期](#生命周期 "生命周期")


```javascript
var vm = new Vue({
  //选择器
  el: '#example',   
  //数据(双向绑定)
  data: {          
    message:"654321"  
    name:"zhangsan", //vm.name
    age:12
  }         
  //生命周期
  created:function(){
    // `this` 指向 vm 实例
  },
  mounted:function () {

  },
  updated:function(){

  },
  destroyed:function () {

  }
  //计算
  computed：{
    computedFun: function () {
      return this.message.split('').reverse().join('');
    }
  }
  //方法
  methods:{
    fun:function(){

    }
  }
  //监测
  watch:{
    watchData:function(){

    }
  }
})

```

## 计算属性
计算属性是基于它们的依赖进行缓存的,只有在它的相关依赖发生改变时才会重新求值;计算属性默认只有 getter ，不过在需要时你也可以提供一个 setter 。
```javascript
// JavaScript
var vm = new Vue({
  el: '#example',
  data: {
    message: 'Hello'
  },
  computed: {
    // getter
    getFun: function () {
      // `this` points to the vm instance
      return this.message.split('').reverse().join('');
    }
    // setter
    setFun: function (newValue) {
      var names = newValue.split(' ');
      this.firstName = names[0];
      this.lastName = names[names.length - 1];
    }
  }
})
```
```HTML
<!-- HTML -->
<p>Original message: "{{ message }}"</p>
<p>Computed reversed message: "{{ reversedMessage }}"</p>
<!-- 只要 message 还没有发生改变，多次访问 reversedMessage 计算属性会立即返回之前的计算结果，而不必再次执行函数 -->
```
**【注意】** 我们为什么需要缓存？假设我们有一个性能开销比较大的的计算属性 A ，它需要遍历一个极大的数组和做大量的计算。然后我们可能有其他的计算属性依赖于 A 。如果没有缓存，我们将不可避免的多次执行 A 的 getter！如果你不希望有缓存，请用 method 替代。
**【注意】** 当你有一些数据需要随着其它数据变动而变动时，很容易滥用 watch 。然而，通常更好的想法是使用 computed 属性而不是命令式的 watch 回调。



## methods
只要发生重新渲染，method 调用定义的函数
```javascript
// JavaScript
var vm = new Vue({
  el: '#example',
  data: {
    message: 'Hello'
  },
  methods: {
    // a computed getter
    reversedMessage: function () {
      // `this` points to the vm instance
      return this.message.split('').reverse().join('');
    }
  }
})
```
```HTML
<!-- HTML -->
<p>Original message: "{{ message }}"</p>
<p>Computed reversed message: "{{ reversedMessage }}"</p>
<!-- 只要发生重新渲染，method 调用总会执行reversedMessage函数 -->
```

## watch
当你想要在数据变化响应时，执行异步操作或开销较大的操作，使用watch监测是很有用的。
```javascript
// JavaScript
var vm = new Vue({
  watch: {
    // a computed getter
    getData: function () {
      $.ajax({
        ...
      })
    }
  }
})
```

## 生命周期
![vue生命周期图例](amWiki/images/vue_lifecycle.jpg)
