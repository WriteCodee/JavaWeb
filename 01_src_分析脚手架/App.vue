<template>
  <div>  <!-- 必须有这个div -->
    <img src="./assets/logo.png" alt="logo">
    <school></school>
    <Student></Student>
  </div>
</template>

<script>
    // 引入组件
    import School from './components/School_Test.vue'
    import Student from './components/Student_Test.vue'
    export default {
        name:"App",

        // 注册组件
        components:{
            School,
            Student
        }
    }
</script>

<style>

</style>