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
       el: '#app',
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
        el: '#app',
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
        el: '#app',
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
     el: '#app',
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
  <div>{{count}}</div>
 </div>
 <script>
   new Vue(
      el: '#app',
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

#  v-if、v-show、v-for
v-if 控制标签及其内容的显示和不显示
v-show 控制标签及其内容的显示和隐藏
if是通过添加dom和删除dom实现显隐，show是通过给标签添加隐藏属性显隐。if会删除标签show不会

```html
<body>
  <div id='app'>
  <div v-if='flag'>
    {{msg}}
  </div>
   </div>
  <script>
    new Vue(
      el: '#app',
      data: {
          msg: '',
          flag: false
      }
      
    )
  </script>
</body>
```
# v-for

```html
<body>
  <div id='app'>
      <ul>
        <li v-for="(item,index) in list" :key="index">{{item}}_索引：{{index}}</li>
      </ul>
  </div>
  <script>
      new Vue(
          el: '#app',
          data: {
            msg: "Hello World",
            list: [1,2,3,4]
          }
      )
  </script>
</body>
```

# to_do list

```html
  <body>
    <div id="app">
      <input v-model='task'/>
      <ul>
        <li v-for= "(item,index) in list" :kay="index">{{item}}</li>
      </ul>
    </div>
    
    <script>
      new Vue(
        el: "#app",
        data: {
          task: "",  
        },
        method: {
          onSubmit: function(){
             if(this.task == ''){
                return;
             }
             this
          }
        }
      )
    </script>  
  </body> 
```

#  组件，全局组件与局部组件，父组件向子组件传值
```html
<body>
  <div id="app">
    <ul>
      <todo-item2 v-for="(item,index) in tasklist" :key="index" :item="item"></todo-item2>
    </ul>
  </div>
  <script>
    Vue.component(
      'todo-item,{
        props: ['item'],
        template：'<li>{{item}}</li>'
      }  
    );
    var localItemComponent = {
      props: ['item'],
      template: '<li>{{item}}</li>'
    }
    
    new Vue({
      el: "#app",
      components:{
         toto-item2: localItemComponent 
      },
      data:{
        tasklist: ['1','2','3','4']
      }
      }
    )
  </script>
</body>
```
# 钩子函数
```html
  <body>
    <div id="app">
      <div> 
        <input type='text' v-focus/>
        <div v-color='msg'></div>
      </div>
    </div>
    <script>
      Vue.directive('focus',{
        inserted(el){
          el.focus()
        }
      }
      ),
      Vue.directive('color',{
        inserted(el,binding){
             el.style.backgroundColor = binding.value.color;
        }
      }   
      ),
      var vm = new Vue({
          el:"#app",
          data:{
             color:'blue'
          }
      }
      )
    </script>
  </body>
```
