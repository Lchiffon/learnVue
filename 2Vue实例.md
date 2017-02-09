# VUE.JS

有用的链接:
- [Vue生态库](https://github.com/vuejs/awesome-vue#libraries--plugins)
- [Github](https://github.com/vuejs/vue)
- [在线编辑器](https://jsfiddle.net/chrisvfritz/50wL7mdz/)
- [中文VUE教程网站](https://cn.vuejs.org)
- [API文档](https://cn.vuejs.org/v2/api)

## Vue实例
### 构造器
1. 使用: `new Vue({})`
2. 可复用的构造器:

```JS
var myComponent = Vue.extend({
  //扩展选项
})
var myComponentInstance = new MyComponent
```
建议使用自定义元素而不是可复用构造器

### 属性与方法
1. 每个实例都会自动**代理**data中的对象的所有属性
2. 只有data的对象是可以被**代理**的

#### 示例1
```JS
var data = {a:1}
var vm = new Vue({
  data: data
})

data.a==vm.a
//设置属性会影响原始数据
vm.a=2
data.a
//2

//设置原始数据也会影响Vue对象
data.a=3
vm.a
```

#### 示例2
```JS
var data = {a:1}
var vm = new Vue({
  el: "#example",
  data: data
})

vm.$data === data
vm.$el === document.getElementById('example')

// $watch是一个实例方法
vm.$watch('a', function(newVal,oldVal){
  //该方法将在`vm.a改变后被调用`
})
```

### 实例生命周期
create->mounted->updated->destroyed

`this`用于指向调用它的实例
![](https://cn.vuejs.org/images/lifecycle.png)
