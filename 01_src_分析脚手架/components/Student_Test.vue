<template>
    <!-- 组件的结构 -->
    <div class="demo1">
        <h2>学生姓名：{{studentName}}</h2>
        <h2>学生年龄：{{studentAge}}</h2>
        <button @click="showInfo">点我提示学生信息</button>
    </div>
</template>

<script>
    // 组件的交互信息
    export default {
        name:"Student_Test",
        data() {
            return {
                studentName:"小明",
                studentAge:18
            }
        },
        methods: {
            showInfo(){
                alert(this.studentName,this.studentAge)
            }
        },
    }
</script>

<style>
    /* 组件的样式 */
    .demo1{
        background-color: peru;
    }
</style>