<template>
    <div>
        <h2 @click="showName">学校名称：{{ name }}</h2>
        <h2>学校地址：{{address}}</h2>
    </div>
</template>

<script>
// 引入自己写的文件，mixin.js : 这是局部混合
import { mixin,mixin2 } from '../mixin';
export default {
    name: "SchoolVue",
    data() {
        return {
            name:"尚硅谷",
            address:"北京"
        }
    },
    // 配置项来配置mixin
    mixins:[mixin,mixin2]

   
}
</script>

