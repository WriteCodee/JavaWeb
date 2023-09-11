<template>
    <div>
        <h1>{{ msg }}</h1>
        <h2>学生姓名:{{ name }}</h2>
        <h2>学生性别:{{ sex }}</h2>
        <h2>学生年龄:{{ myAge + 1 }}</h2>
        <button @click="updateAge"> 尝试修改收到的年龄 </button>
    </div>
</template>

<script>
export default {
    name: "StudentVue",
    data() {
        return {
            msg: "他是一个学生",
            myAge: this.age
        }
    },
    methods: {
        updateAge() {
            console.log(this.myAge)
            this.myAge++
        }
    },
    // 简单接收
    /* props:['name','sex','age'] // 外部传进来的数据(简单接收) */

    // 接受的同时对数据进行类型限制
    /* props:{
        name:String,
        sex:String,
        age:Number
    } */
    // 接收数据的同时进行类型限制+默认值的指定+必要性的限制
    props: {
        name: {
            type: String,     // name的类型是字符串
            required: true    // name必须传入
        },
        age: {
            type: Number,     // age的类型是数字
            default: 99       // 默认是99
        },
        sex: {
            type: String,
            required: true
        }
    }

}
</script>

