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
Vue所有的生命周期钩子自动绑定在this上下文到实例中，因此你可以访问数据，对属性和方法进行运算。这意味着你不能使用箭头函数来定义一个生命周期方法。这是因为箭头函数绑定了父上下文，因此this与你期待的Vue实例不同。
### beforeCreate
在实例初始化之后，数据观测和event/watcher时间配置之前被调用。
### created
实例已经创建完成之后被调用。在这一步，实例已经完成以下的配置：数据观测，属性和方法的运算，watch/event事件回调。然而，挂载阶段还没开始，$el属性目前不可见。
### beforeMount
在挂载开始之前被调用：相关的render函数首次被调用。<br>
该钩子在服务器端渲染期间不被调用。
### mounted
el被新创建的vm.$el替换，并挂在到实例上去之后调用该钩子函数。如果root实例挂载了一个文档内元素，当mounted被调用时vm.$el也在文档内。<br>
该钩子在服务端渲染期间不被调用。
### beforeUpdate
数据更新时调用，发生在虚拟DOM重新渲染和打补丁之前。<br>
你可以在这个钩子中进一步第更改状态，这不会触发附加的重渲染过程。<br>
该钩子在服务端渲染期间不被调用。
### updated
由于数据更改导致的虚拟DOM重新渲染和打补丁，在这之后会调用该钩子。<br>
当这个钩子被调用时，组件DOM已经更新，所以你现在可以执行依赖于DOM的操作。然而在大多数情况下，你应该避免在此期间更改状态，因为这可能会导致更新无限循环。<br>
该钩子在服务端渲染期间不被调用。
### activated
keep-alive组件激活时调用。<br>
该钩子在服务器端渲染期间不被调用。
### deactivated
keep-alive组件停用时调用。<br>
该钩子在服务端渲染期间不被调用。
### beforeDestroy 【类似于React生命周期的componentWillUnmount】
实例销毁之间调用。在这一步，实例仍然完全可用。<br>
该钩子在服务端渲染期间不被调用。
### destroyed
Vue实例销毁后调用。调用后，Vue实例指示的所有东西都会解绑定，所有的事件监听器会被移除，所有的子实例也会被销毁。<br>
该钩子在服务端渲染不会被调用。
![vue生命周期图例](amWiki/images/vue_lifecycle.jpg)
