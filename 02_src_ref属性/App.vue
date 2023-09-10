<template>
  <div>
    <h1 v-text="msg" ref="title"></h1>
    <button ref="btn" @click="showDOM">点我输出上方的DOM元素</button>
    <SchoolVue ref="sch"></SchoolVue>
  </div>
</template>

<script>
    // App.vue汇总所有组件,所以引入SchoolVue组件
    import SchoolVue from './components/SchoolVue.vue'
    export default {
        name:"App",
        data() {
          return {
            msg:"欢迎学习Vue"
          }
        },
        methods: {
          showDOM(){
            // console.log(document.getElementById("title"))  // 可以这么写,但是不合适,所以不用id,用ref
            console.log(this.$refs.title)  // 真实DOM元素
            console.log(this.$refs.btn)    // 真实DOM元素
            console.log(this.$refs.sch)    // School组件的实例对象(vc)

          }
        },
        // 注册组件
        components:{
            SchoolVue
        }
    }
</script>

<style>

</style>