<template>
    <div class="todo-footer" v-show="total"> <!-- v-show：如果total是0，那么是false。就不展示整个div，也就是没有一个待办任务 -->
        <label>
            <!-- <input type="checkbox" :checked="isAll" @change="checkAll"/> -->
            <input type="checkbox" v-model="isAll" />
        </label>
        <span>
            <span>已完成{{ doneTotal }}</span> / 全部{{ total }}
        </span>
        <button class="btn btn-danger" @click="clearAll">清除已完成任务</button>
    </div>
</template>

<script>
export default {
    name: "MyFooter",

    props: ["todoList", "checkAllTodo","deleteAllTodo"],
    methods: {
        // checkAll(e) {
        //     this.checkAllTodo(e.target.checked)
        // }
        clearAll(){
            this.deleteAllTodo()
        }
    },
    computed: {
        total() {
            return this.todoList.length
        },
        doneTotal() {
            return this.todoList.reduce((pre, current) => { return pre + (current.done ? 1 : 0) }, 0)
        },
        // 计算属性：简写只能读取，不能修改；想要修改必须写成get，set
        isAll: {
            get(){
                return this.doneTotal === this.total && this.total > 0
            },
            set(value){
                this.checkAllTodo(value)
            }

        }
    }
}
</script>

<style scoped>
/*footer*/
.todo-footer {
    height: 40px;
    line-height: 40px;
    padding-left: 6px;
    margin-top: 5px;
}

.todo-footer label {
    display: inline-block;
    margin-right: 20px;
    cursor: pointer;
}

.todo-footer label input {
    position: relative;
    top: -1px;
    vertical-align: middle;
    margin-right: 5px;
}

.todo-footer button {
    float: right;
    margin-top: 5px;
}
</style>