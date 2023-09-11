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

```
打标识:<h1 ref="xxx">......</h1> 或者 <SchoolVue ref="xxx"></SchoolVue>
获取:this.$refs.xxx
```



## mixin(混入)

**功能：**可以把多个组件共用的配置提取成一个混入的对象
		**使用方式：**

		第一步：定义混合，例如	：
			{
				data(){...},
				methods:{...},
				...
			}
		第二步：使用混合，例如：
			(1)全局混入：Vue.mixin(xxx)
			(2)局部混入：mixin:['xxx']
## plugins(插件)

**功能：**用于增强Vue
		**本质：**包含install方法的一个对象，install的第一个参数是Vue，第二个以后的参数是插件使用传递者传递的数据
		**定义插件：**

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

**使用插件：**Vue.use(插件名)

## scoped样式

**作用：**让样式局部生效，防止冲突

    写法：<style scoped>
          </style>