<template>
  <div>
    <SchoolVue></SchoolVue>
    <hr>
    <StudentVue></StudentVue>
  </div>
</template>

<script>
    // App.vue汇总所有组件,所以引入SchoolVue组件
    import SchoolVue from './components/SchoolVue.vue';
    import StudentVue from './components/StudentVue.vue'
    export default {
        name:"App",
        // 注册组件
        components:{
            StudentVue,
            SchoolVue
        }
    }
</script>

<style>

</style>