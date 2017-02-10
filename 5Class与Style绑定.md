# VUE.JS

有用的链接:
- [Vue生态库](https://github.com/vuejs/awesome-vue#libraries--plugins)
- [Github](https://github.com/vuejs/vue)
- [在线编辑器](https://jsfiddle.net/chrisvfritz/50wL7mdz/)
- [中文VUE教程网站](https://cn.vuejs.org)
- [API文档](https://cn.vuejs.org/v2/api)

## Class与Style绑定
### 绑定HTML Class
#### 对象语法
可以传给`v-bind:class`一个对象, 以动态切换class:
```html
<div v-bind:class="{active: isActive}"></div>
```
`active`是否成为该div的class取决于isActive的属性值.

另一个例子:
```html
<div class='static'
  v-bind:class='{active: isActive, 'text-danger': hasError}'>
</div>
```
```js
var vm = new Vue({
  el='#static',
  data = {
    isActive: true,
    hasError: false
  }
})
```
同样Vue也可以绑定数据中的一个对象来实现上述功能.
```html
<div v-bind:class="classObject"></div>
```
```js
data:{
  classObject: {
    active: true,
    'text-danger': false
  }
}
```
更深入一步, 可以在这里绑定计算属性,以达到同样的目的:
```html
<div v-bind:class="classObject"></div>
```
```js
data:{
  isActive: true,
  error: null
},
computed: {
  classObject: function(){
    return{
      active: this.isActive && !this.error,
      'text-danger': this.error && this.error.type === 'fatal'
    }
  }
}
```
#### 数组语法
可以对`v-bind:class`传一个数组, 以应用一个class列表.
```html
<div v-bind:class="[activeClass, errorClass]"></div>
```
```js
data:{
  activeClass: 'active',
  errorClass: 'text-danger'
}
```
或者三元表达式:
```html
<div v-bind:class="[isActive ? activeClass : "", errorClass]"
```

### 内联样式
#### 对象语法
使用`v-bind:style`绑定样式
1. 使用属性绑定
2. 绑定对象
3. 绑定数组

```html
<div v-bind:style="{color: activeColor,
fontSize: fontSize + 'px'}"></div>
<!--对象绑定-->
<div v-bind:style="styleObject"></div>
<!--绑定数组-->
<div v-bind:style="[baseStyles, overrodomgStyles]"></div>
```
```js
data:{
  activeColor:'red',
  fontSize: 12,
  styleObject:{
    color: 'red',
    fontSize: '13px'
  }
}
```
