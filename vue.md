# 查看版本
$ npm -v
2.3.0

# 升级 npm
cnpm install npm -g


# 升级或安装 cnpm
npm install cnpm -g

# 点击事件
  @click （也可以使用v-on:click）
```html
  <body>
    <div id="app">
     <div @click='handleClick'>{{msg}}</div>
    </div>
    <script>
      new Vue({
       el: 'app',
       data: {
         msg: "hello world"
       },
       methods: {
        handleClick: function(){
           this.msg = this.msg+ "click";
        }
       }
       }
       )
   </script>
  </body>
```

# 双向绑定机制
双向绑定就是页面的值影响vue实例中的值，实例中的值也影响页面上的值。
```html
<body>
  <div id="app">
    <div v-on:click="handler">事件绑定事例</div>
    <div @click="handler">事件绑定事例</div>
    <input type="text" v-model="value"/>
    <div id="app" v-text="value">
    <p>value的值是 {{value}} </p>
  </div>
  <script src="js/vue.js"></script>
  <script>
      const vm = new Vue({
        el: 'app',
        data: {
          value: ''
          }
        },
      )
  </script>
</body>
```

# 单向绑定
单向绑定就是实例中的值影响页面的值，页面的值不影响实例中的值
```html 
<body>
 <div id= "app">
   <input v-bind:value='value'/>
 </div> 
 <script>
    const vm = new Vue({
        el: 'app',
        data: {
          value: ''
        }
    })
 </script>
</body>
```
# 计算器
  如果data中没有对应属性，则从计算属性中获取。computed计算器属性相当于加了一层缓存，只有当里面用到的变量值变化时才会重新计算，否则从缓存获取，
  所以应该尽量使用computed，不应使用{{}}{{}}的方式。
```html
<body>
 <div id="app">
   <input v-model="firstname"/>
   <input v-model="lastname"/>
  <div>{{fullname}}</div>
 </div>
 <script>
   new Vue({
     el: 'app',
     data: {
       firstname: "",
       lastname: ""
    },
    computed: {
       fullname: function(){
         return this.firstname +""+ this.lastname
       }
    }
  })
 </script>
</body>
```

# 监听器

```html
<body>
 <div id="app">
  <input v-model="firstname"/>
  <input v-model="secondname"/>
  <div></div>
 </div>
 <script>
   new Vue(
      el: 'app',
      data: {
        firstname: "",
        secondname:"",
        count: 0
      },
      watch: {
        firstname: function(){
          this.count = this.count++; 
       },
       secondname: function(){
          this.count = this.count++; 
       }
      }
  )
 </script>
</body>
```





