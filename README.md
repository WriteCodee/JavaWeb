# vue_test

## 脚手架文件结构：

```javascript
node_modules
public 
	favicon.ico:页签图标
	index.html：主页面
src
	assets：存放静态资源
		logo.png
	component：存放组件
		HelloWorld.vue
	App.vue：汇总所有组件
	main.js：入口文件
.gitignore：git版本控制忽略的配置
babel.config.js：babel的配置文件
package.json：应用包配置文件
README.md：应用描述文件
package-lock.json：包版本控制文件
```

## 关于不同版本的Vue：

* vue.js与vue.runtime.xxx.js的区别:

     (1) vue.js 是完整版的Vue,包含:核心功能+模板解析器

     (2) vue.runtime.xxx.js是运行版的Vue,只包含:核心功能;没有模板解析器

* 因为vue.runtime.js没有模板解析器,所以不能使用template配置项,需要使用

  render函数接收到的createElement函数去指定具体内容。

## Vue.config.js配置文件

> 使用vue inspect > output.js 可以查看Vue脚手架的默认配置

> 使用vue.config.js可以对脚手架进行个性化定制

https://cli.vuejs.org/zh

## ref属性
1.被用来给元素或子组件注册引用信息(document.getElementById的代替者)
		2.应用在html标签上获取的是真实DOM元素,应用在组件标签上是组件实例对象(vc)
		3.使用方式:

```vue
打标识:<h1 ref="xxx">......</h1> 或者 <SchoolVue ref="xxx"></SchoolVue>
获取:this.$refs.xxx
```



## mixin(混入)

**功能：**可以把多个组件共用的配置提取成一个混入的对象
		**使用方式：**

```vue
	第一步：定义混合，例如	：
		{
			data(){...},
			methods:{...},
			...
		}
	第二步：使用混合，例如：
		(1)全局混入：Vue.mixin(xxx)
		(2)局部混入：mixin:['xxx']
```
## plugins(插件)

**功能：**用于增强Vue
		**本质：**包含install方法的一个对象，install的第一个参数是Vue，第二个以后的参数是插件使用传递者传递的数据
		**定义插件：**

```vue
	对象.install = function(Vue,options){
		// 全局过滤器
    Vue.filter('mySlice',function(value){
        return value.slice(0,4)
    })
    // 定义全局指令
    Vue.directive('fbind',{
        // 指令与元素成功绑定时（一上来）
        bind(element,binding){
            element.value = binding.value
        },
        // 指令所在元素被插入页面时
        inserted(element,bindings){
            element.focus()
        },
        // 指令与所在的模板被重新解析时
        update(element,binding){
            element.value = binding.value
        }
    })

    // 定义混入
    Vue.mixin({
        data(){
            return{
                x:100,
                y:200
            }
        }

    })
    // 给Vue原型上添加一个方法（vm和vc就都能用了）
    Vue.prototype.hello=()=>{alert("你好啊")}
	}
```

**使用插件：**Vue.use(插件名)

## scoped样式

**作用：**让样式局部生效，防止冲突

```vue
写法：<style scoped>
      </style>
```

## 总结TodoList案例

1.组件化编码流程：

​	（1）拆分静态组件：组件要按照功能点拆分，命名不要与html元素冲突。

​	（2）实现动态组件：考虑好数据的存放位置，数据是一个组件在用，还是一些组件在用：

​			1）一个组件在用：放在组件自身即可

​			2）一些组件在用：放在他们共同的父组件上（状态提升）

​	（3）实现交互：从绑定事件开始

2.props适用于：

​	（1）父组件 ==> 子组件 通信

​	（2）子组件 ==> 父组件 通信（要求父先给子一个函数）

3.使用v-model时要切记：v-model绑定的值不能是props传过来的，因为props是不可以修改的！

4.props传过来的若是对象类型的值，修改对象中的属性时Vue不会报错，但不推荐这样做。

## WebStorage

1.存储内容大小一般支持5MB左右（不同浏览器可能不一样）

2.浏览器端通过Window.sessionStorage 和 Window.localStorage属性来实现本地存储机制

3.相关API：

​		1.xxxxxStorage.setItem('key','value')

​				该方法接受一个键和值作为参数，会把键值对添加到存储中，如果键名存在，则更新其对应的值

​		2.xxxxxStorage.getItem('key')

​				该方法接受一个键名作为参数，返回键名对应的值

​		3.xxxxxStorage.removeItem('key')

​				该方法接受一个键名作为参数，并把该键名从存储中删除

4.备注：

​		1.SessionStorage存储的内容会随着浏览器窗口关闭而消失

​		2.LocalStorage存储的内容，需要手动清楚才会消失

​		3.xxxxxStorage.getItem(xxx)如果xxx对应的value获取不到，那么getItem的返回值是null

​		4.JSON.parse(null)的结果依然是null
