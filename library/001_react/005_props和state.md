# 状态保存/数据传递
## props
- 组件的外部状态
- 通常用来保存固定的数据

#### 外部状态的获取
```javascript
this.props.key
```

## state
- 组件的内部状态
- 通常用来保存变化的数据
- 一旦内部状态发生改变，就会发生局部更新，react会比对上次state的值，如果改变，就会重新渲染

#### 内部状态的获取
```javascript
this.state.key
```

#### 内部状态的设置/修改
>setState :
合并内部状态(不存在的添加，存在的修改)

```javascript
this.setState({
  key:value
})

this.setState(function(data){ //data保存上一次的state值
  return {
    key:data.key-1
  }
})
```
