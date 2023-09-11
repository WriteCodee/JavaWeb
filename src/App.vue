<template>
  <div>
    <!-- 使用:age -->
    <student-vue name="李四" sex="女" :age=19></student-vue>   
    <hr>
    <student-vue name="王五" sex="男" :age=20></student-vue>
    <hr>
  </div>
</template>

<script>
    // App.vue汇总所有组件,所以引入SchoolVue组件
    import StudentVue from './components/StudentVue.vue'
    export default {
        name:"App",
        // 注册组件
        components:{
            StudentVue
        }
    }
</script>

<style>

</style>