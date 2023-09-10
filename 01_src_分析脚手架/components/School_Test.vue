<!-- 命名的时候，如果是多个单词，最好每个单词的开头都大写，和开发者工具中的呼应上 -->
<template>
    <!-- // 组件的结构 -->
    <div class="demo">
        <h2>学校名称：{{ schoolName }}</h2>
        <h2>学校地址：{{ address }}</h2>
        <button @click="showName">点我提示学校名</button>
    </div>
</template>

<script>
// 组件交互相关的代码（数据、方法）

export default {
    // el:"#root",定义组件时一定不要写el配置项，因为最终所有的组件都要被一个vm管理，由vm决定服务于哪个容器
    name: "School_Test",
    data() {
        return {
            schoolName: "尚硅谷",
            address: "北京"
        }
    },
    methods: {
        showName() {
            alert(this.schoolName)
        }
    },
}

</script>

<style>
/* 组件的样式 */
.demo {
    background-color: orange;
}
</style>
