<template>
    <div>
        <h2>学校名称：{{ name | mySlice }}</h2>
        <h2>学校地址：{{address}}</h2>
        <button @click="TestHello">点我测试一下Hello方法</button>
    </div>
</template>

<script>
export default {
    name: "SchoolVue",
    data() {
        return {
            name:"尚硅谷atguigu",
            address:"北京"
        }
    },
    methods:{
        TestHello(){
            this.hello()
        }
    }
   
}
</script>

