
- [Vue](#vue)
  - [开发流程](#%e5%bc%80%e5%8f%91%e6%b5%81%e7%a8%8b)
  - [data](#data)
  - [$set](#set)
  - [vue实例](#vue%e5%ae%9e%e4%be%8b)
  - [指令](#%e6%8c%87%e4%bb%a4)
      - [v-once](#v-once)
      - [v-text](#v-text)
      - [v-html](#v-html)
      - [v-model](#v-model)
      - [v-bind](#v-bind)
      - [v-if与v-show的区别](#v-if%e4%b8%8ev-show%e7%9a%84%e5%8c%ba%e5%88%ab)
      - [遍历(v-for)](#%e9%81%8d%e5%8e%86v-for)
  - [在vue中什么时候使用或不用箭头函数](#%e5%9c%a8vue%e4%b8%ad%e4%bb%80%e4%b9%88%e6%97%b6%e5%80%99%e4%bd%bf%e7%94%a8%e6%88%96%e4%b8%8d%e7%94%a8%e7%ae%ad%e5%a4%b4%e5%87%bd%e6%95%b0)
  - [axios 和 promise 的理解](#axios-%e5%92%8c-promise-%e7%9a%84%e7%90%86%e8%a7%a3)
  - [css 预处理器 以及 css新特性 的了解](#css-%e9%a2%84%e5%a4%84%e7%90%86%e5%99%a8-%e4%bb%a5%e5%8f%8a-css%e6%96%b0%e7%89%b9%e6%80%a7-%e7%9a%84%e4%ba%86%e8%a7%a3)
  - [事件](#%e4%ba%8b%e4%bb%b6)
      - [事件监听](#%e4%ba%8b%e4%bb%b6%e7%9b%91%e5%90%ac)
      - [事件处理方法](#%e4%ba%8b%e4%bb%b6%e5%a4%84%e7%90%86%e6%96%b9%e6%b3%95)
      - [参数传递](#%e5%8f%82%e6%95%b0%e4%bc%a0%e9%80%92)
      - [事件修饰符](#%e4%ba%8b%e4%bb%b6%e4%bf%ae%e9%a5%b0%e7%ac%a6)
      - [自定义按键修饰符](#%e8%87%aa%e5%ae%9a%e4%b9%89%e6%8c%89%e9%94%ae%e4%bf%ae%e9%a5%b0%e7%ac%a6)
      - [表单基本操作](#%e8%a1%a8%e5%8d%95%e5%9f%ba%e6%9c%ac%e6%93%8d%e4%bd%9c)
  - [表单域修饰符用法](#%e8%a1%a8%e5%8d%95%e5%9f%9f%e4%bf%ae%e9%a5%b0%e7%ac%a6%e7%94%a8%e6%b3%95)
  - [自定义指令](#%e8%87%aa%e5%ae%9a%e4%b9%89%e6%8c%87%e4%bb%a4)
  - [计算属性](#%e8%ae%a1%e7%ae%97%e5%b1%9e%e6%80%a7)
  - [计算属性 vs 方法](#%e8%ae%a1%e7%ae%97%e5%b1%9e%e6%80%a7-vs-%e6%96%b9%e6%b3%95)
  - [计算属性 vs 侦听器（侦听属性）](#%e8%ae%a1%e7%ae%97%e5%b1%9e%e6%80%a7-vs-%e4%be%a6%e5%90%ac%e5%99%a8%e4%be%a6%e5%90%ac%e5%b1%9e%e6%80%a7)
  - [过滤器](#%e8%bf%87%e6%bb%a4%e5%99%a8)
  - [vue生命周期有哪些](#vue%e7%94%9f%e5%91%bd%e5%91%a8%e6%9c%9f%e6%9c%89%e5%93%aa%e4%ba%9b)
  - [数组API](#%e6%95%b0%e7%bb%84api)
  - [动态数组响应式数据](#%e5%8a%a8%e6%80%81%e6%95%b0%e7%bb%84%e5%93%8d%e5%ba%94%e5%bc%8f%e6%95%b0%e6%8d%ae)




# Vue

## 开发流程
- 声明式渲染>组件統>客户端路由→集中式状态管理>项目构建

## data
- Vue 实例的数据对象。

## $set

## vue实例
- 初始化
 ```js
  <!-- View 视图 -->
    <div id="app">
        {{msg}} //moustache 小胡子语法
    </div>

  // 使用vue的构造方法创建vue实例
      let vm = new Vue({
          el: "#app", // 挂载点，用来设置vue实例挂载（管理）的元素
          data: {     // model 数据 , data中的数据被vm所代理
              msg: 'hello vue' // 可以通过vm.msg取到对应内容
          }
      })
  ```
## 指令

#### v-once
- 只渲染元素和组件一次。

#### v-text
- 更新元素的 textContent。
- 如果要更新部分的 textContent ，需要使用 {{ Mustache }} 插值。    
  ```html
  <span v-text="msg"></span>
  <!-- 和下面的一样 -->
  <span>{{msg}}</span>
  ```

#### v-html
- 更新元素的 innerHTML，html字符串渲染成html。
- 只在可信内容上使用 v-html，永不用在用户提交的内容上。
- 因为容易导致 XSS 攻击（跨站恶意脚本）。

#### v-model
- 在表单 `<input>`、`<textarea>` 及 `<select>` 元素上创建双向数据绑定
- 修饰符 
  1. lazy - `在“change”时而非“input”时更新`  
   ```html
   <input v-model.lazy="msg" >
   ```
  2. number - `自动将用户的输入值转为数值类型`
   ```html
   <input v-model.number="age" type="number">
   ```
  3. trim - `自动过滤用户输入的首尾空白字符`
   ```html
   <input v-model.trim="msg">
   ```

#### v-bind
  - 动态地绑定一个或多个特性，或一个组件 prop 到表达式。
  ```html
  <!-- 绑定一个属性 -->
  <img v-bind:src="imageSrc">

  <!-- 动态特性名 (2.6.0+) -->
  <button v-bind:[key]="value"></button>

  <!-- 缩写 -->
  <img :src="imageSrc">

  <!-- 动态特性名缩写 (2.6.0+) -->
  <button :[key]="value"></button>

  <!-- 内联字符串拼接 -->
  <img :src="'/path/to/images/' + fileName">

  <!-- class 绑定 -->
  <div :class="{ red: isRed }"></div>
  <div :class="[classA, classB]"></div>
  <div :class="[classA, { classB: isB, classC: isC }]">

  <!-- style 绑定 -->
  <div :style="{ fontSize: size + 'px' }"></div>
  <div :style="[styleObjectA, styleObjectB]"></div>

  <!-- 绑定一个有属性的对象 -->
  <div v-bind="{ id: someProp, 'other-attr': otherProp }"></div>

  <!-- 通过 prop 修饰符绑定 DOM 属性 -->
  <div v-bind:text-content.prop="text"></div>

  <!-- prop 绑定。“prop”必须在 my-component 中声明。-->
  <my-component :prop="someThing"></my-component>

  <!-- 通过 $props 将父组件的 props 一起传给子组件 -->
  <child-component v-bind="$props"></child-component>

  <!-- XLink -->
  <svg><a :xlink:special="foo"></a></svg>
  ```

#### v-if与v-show的区别
- `vi-if` 控制元素是否渲染到页面
- `v-show` 控制元素是否显示（已经渲染到了页面）
>v-if 是“真正”的条件渲染，因为它会确保在切换过程中条件块内的事件监听器和子组件适当地被销毁和重建。     
>v-if 也是惰性的：如果在初始渲染时条件为假，则什么也不做——直到条件第一次变为真时，才会开始渲染条件块。  
>相比之下，v-show 就简单得多——不管初始条件是什么，元素总是会被渲染，并且只是简单地基于 CSS 进行切换。  
>一般来说，v-if 有更高的切换开销，而 v-show 有更高的初始渲染开销。因此，如果需要非常频繁地切换，则使用 v-show 较好；如果在运行时条件很少改变，则使用 v-if 较好。

#### 遍历(v-for)
- v-for 遍历数组
    ```html
    <li v-for='item in list'>{{item}}</li>
    <li v-for='(item, index) in list'>{{item}} + '---' + {{index}}</1i>
    ```
- key的作用：帮助Vue区分不同的元素，从而提高性能
    ```html
    <li :key='item.id' v-for='(item, index) in list'>{{item}} + '---' {{index}}</li>
    ```
- v-for遍历对象
    ```html
    <div v-for='(value,key,index) in object'></div>
    ```
- v-if和v-for结合使用
    ```html
    <div v-if='value==12' v-for='(value,key,index) in object'></div>
    ```

## 在vue中什么时候使用或不用箭头函数
- 在 vue 的 methods 不能用箭头函数(取不到this)
- 在 axios 回调，用箭头函数，使得回调中的this指向vue实例
  ```js
  axios.get('/user', {
    params: {
      ID: 12345
    }
  })
  .then((response) => {
    console.log(response);
  })
  .catch((error) => {
    console.log(error);
  });
  ```

## axios 和 promise 的理解
## css 预处理器 以及 css新特性 的了解

## 事件

#### 事件监听 
  ```html
    <button v-on:click="doThis"></button>
    
    <!-- 缩写 -->
    <button @click="doThis"></button>
  ```

#### 事件处理方法 

  ```html
    <div id="example-2">
        <!-- `greet` 是在下面定义的方法名 -->
        <button v-on:click="greet">Greet</button>
    </div>
  ```
  ```js
    var example2 = new Vue({
        el: '#example-2',
        data: {
            name: 'Vue.js'
    },
    // 在 `methods` 对象中定义方法
    methods: {
        greet: function (event) {
        // `this` 在方法里指向当前 Vue 实例
        alert('Hello ' + this.name + '!')
        // `event` 是原生 DOM 事件
        if (event) {
            alert(event.target.tagName)
        }
        }
    }
    })

    // 也可以用 JavaScript 直接调用方法
    example2.greet() // => 'Hello Vue.js!'
  ```

#### 参数传递 

  - 如果事件直接绑定函数名称,那么默认会传递事件对象作为事件函数的第一个参数
  - 如果事件绑定函数调用,那么事件对象必须作为最后一个参数显示传递,并且事件对象的名称必须是 `$event`
 
 ```html
 <button v-on:c1ick=hand1e1>点击1</ button>
 <button v-on:click="handle2（123，456，$event）'>点击2</button>
 ```

#### 事件修饰符
  - 事件修饰符
    - `.stop` 阻止冒泡
      ```html
      <a v-on:click.stop="handle">跳转</a> 
      ```
    - `.prevent` 阻止默认行为
      ```html
      <a v-on:click.prevent="handle">跳转</a>
      ```
  - 按键修饰符
    - `.enter` 回车键
      ```html
      <input v-on:keyup.enter='submit'>
      ```
    - `.delete` 删除键
      ```html
      <input v-on:keyup.delete= 'handle'>
      ```

 #### 自定义按键修饰符
  - 全局 config.keyCodes对象
    ```js
    Vue.config.keyCodes.fl = 112  
    ```

#### 表单基本操作
- 文本框
  ```html
    <input type="text" v-model='uname'>
  ```
- 单选
  ```html
    <span>
        <input type="radio" id="male" value="1" v-model='gender'>
        <label for="male">男</label>
        <input type="radio" id="female" value="2" v-model='gender'>
        <label for="female">女</label>
    </span>
  ```
- 多选
  ```html
    <div>
        <span>爱好：</span>
        <input type="checkbox" id="ball" value="1" v-model='hobby'>
        <label for="ball">篮球</label>
        <input type="checkbox" id="sing" value="2" v-model='hobby'>
        <label for="sing">唱歌</label>
        <input type="checkbox" id="code" value="3" v-model='hobby'>
        <label for="code">写代码</label>
    </div>
  ```
- 选择框
  ```html
    <select v-model='occupation' multiple>
        <option value="0">请选择职业...</option>
        <option value="1">教师</option>
        <option value="2">软件工程师</option>
        <option value="3">律师</option>
    </select>
  ```
- 文本域
  ```html
    <textarea v-model='desc'></textarea>
  ```

## 表单域修饰符用法
- 转化为数值
  ```html
    <input type="text" v-model.number='age'>
  ```
- 去掉开始和结尾的空格
  ```html
    <input type="text" v-model.trim='info'>
  ```
- 将input事件转换为change事件
  ```html
    <input type="text" v-model.lazy='msg'>
  ```

## 自定义指令
- 基本用法
  ```html
    <input type="text" v-focus>
  ```
  ```js
    Vue.directive('focus', {
      inserted: function(el){
        // el表示指令所绑定的元素
        el.focus();
      }
    });
    // 注册局部指令
    directives: {
        focus: {
            // 指令的定义
            inserted: function (el) {
            el.focus()
            }
        }
    }
  ```
- 钩子函数 
  - bind：只调用一次，指令第一次绑定到元素时调用。在这里可以进行一次性的初始化设置。

  - inserted：被绑定元素插入父节点时调用 (仅保证父节点存在，但不一定已被插入文档中)。
  - ... [etc](https://cn.vuejs.org/v2/guide/custom-directive.html#%E9%92%A9%E5%AD%90%E5%87%BD%E6%95%B0 "钩子函数")
- 钩子函数参数
  - el：指令所绑定的元素，可以用来直接操作 DOM。
  - binding：一个对象，包含以下属性：
  - name：指令名，不包括 v- 前缀。
  - value：指令的绑定值，例如：v-my-directive="1 + 1" 中，绑定值为 2。
  - ... [etc](https://cn.vuejs.org/v2/guide/custom-directive.html#%E9%92%A9%E5%AD%90%E5%87%BD%E6%95%B0%E5%8F%82%E6%95%B0 "钩子函数参数")

## 计算属性
- 对于任何复杂逻辑，你都应当使用计算属性
- 简单的理解为:    

    1.计算属性其实就是 Vue 实例的一个属性

    2.计算属性一般依赖传统的 Vue 实例属性

    3.计算属性一般是通过运算得到的属性
## 计算属性 vs 方法
- computed 能实现的，methods 肯定也能够实现。

- 不同之处在于，computed 是基于他的依赖进行缓存的，computed 只有在他的的相关依赖发生改变的时候才会重新计算。    

- 如果他的相关依赖并没有发生改变，每次访问都是返回他的缓存的值。
methods,则是每次触发重新渲染之后，调用方法会再次执行函数。
总结：当我们不希望有缓存的时候，就使用methods

- >计算属性是基于它们的依赖进行缓存的，只有在它相关的依赖发生改变时才会重新求值，即计算属性会对计算出来的结果进行缓存，这就意味着只要 message 还没有发生改变，多次访问 reversedMessage 计算属性会立即返回之前的计算结果，而不必再次执行函数

  >方法是每次重新渲染时，调用方法将总会再次执行函数，开销比较大 

## 计算属性 vs 侦听器（侦听属性）
- computed 和 watch 的相同和不同之处
  - 相同点：computed 和 watch 都是以vue的依赖追踪为基础的，都是希望当依赖发生改变的时候，被依赖的数据根据预定好的函数发生改变。
  - 不同点：watch 监听，一般是监听一个数据，从而影响多个数据

- computed 计算属性， 一般是计算一个属性，这个属性受多个数据影响

- 总结：一般使用computed,但是如果需要异步，或者数据开销太大的情况下，使用watch.

## 过滤器
- 过滤器是对即将显示的数据做进一步的筛选处理，然后进行显示，值得注意的是过滤器并没有改变原来的数据，只是在原数据的基础上产生新的数据。
- 定义过滤器   
  - 全局过滤器
    ```
    Vue.filter('过滤器名称', function (value1[,value2,...] ) {  
        //逻辑代码
    })
    ```
  - 局部过滤器
    ```
        new Vue({       
            filters: {      
                '过滤器名称': function (value1[,value2,...] ) { 
                    // 逻辑代码     
                } 
            }    
    　　})
    ``` 

- 过滤器使用的地方
  - 双花括号插值
  - v-bind表达式
  ```
    <!-- 在双花括号中 -->
    <div>{{数据属性名称 | 过滤器名称}}</div>
    <div>{{数据属性名称 | 过滤器名称(参数值)}}</div>
    <!-- 在 `v-bind` 中 -->
    <div v-bind:id="数据属性名称 | 过滤器名称"></div>
    <div v-bind:id="数据属性名称 | 过滤器名称(参数值)"></div>
  ```

- [过滤器相关博客文章](https://www.cnblogs.com/shenjianping/p/11330126.html)

## vue生命周期有哪些

| beforeCreate  | 在实例初始化之后，数据观测和事件配置之前被调用 此时data 和 methods 以及页面的DOM结构都没有初始化   什么都做不了                    |
| ------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| created       | 在实例创建完成后被立即调用此时data 和 methods已经可以使用  但是页面还没有渲染出来                                                  |
| beforeMount   | 在挂载开始之前被调用   此时页面上还看不到真实数据 只是一个模板页面而已                                                             |
| mounted       | el被新创建的vm.$el替换，并挂载到实例上去之后调用该钩子。  数据已经真实渲染到页面上  在这个钩子函数里面我们可以使用一些第三方的插件 |
| beforeUpdate  | 数据更新时调用，发生在虚拟DOM打补丁之前。   页面上数据还是旧的                                                                     |
| updated       | 由于数据更改导致的虚拟DOM重新渲染和打补丁，在这之后会调用该钩子。 页面上数据已经替换成最新的                                       |
| beforeDestroy | 实例销毁之前调用                                                                                                                   |
| destroyed     | 实例销毁后调用                                                                                                                     |

## 数组API
- 变异数组    

    | 数组API   | 作用                                                                                                                 |
    | --------- | -------------------------------------------------------------------------------------------------------------------- |
    | push()    | 添加元素                                                                                                             |
    | pop()     | 删除最后一个元素                                                                                                     |
    | shift()   | 删除第一个元素                                                                                                       |
    | unshift() | 添加一个元素到数组最前面                                                                                             |
    | splice()  | splice() 方法通过删除或替换现有元素或者原地添加新的元素来修改数组,并以数组形式返回被修改的内容。此方法会改变原数组。 |
    | sort()    | 排序（升序）                                                                                                         |
    | reverse() | 排序（降序）                                                                                                         |

- 替换数组  
  
    | 数组API  | 作用                                                                                                                                |
    | -------- | ----------------------------------------------------------------------------------------------------------------------------------- |
    | filter() | 数组元素过滤                                                                                                                        |
    | concat() | 连接数组                                                                                                                            |
    | slice()  | slice() 方法返回一个新的数组对象，这一对象是一个由 begin 和 end 决定的原数组的浅拷贝（包括 begin，不包括end）。原始数组不会被改变。 |

## 动态数组响应式数据

- Vue.set(a,b,c)    让 触发视图重新更新一遍，数据动态起来
- a是要更改的数据 、   b是数据的第几项、   c是更改后的数据
