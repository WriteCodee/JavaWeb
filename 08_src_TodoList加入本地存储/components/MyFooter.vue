<template>
  <div class="todo-footer" v-show="total">
    <label>
      <!-- 这样也可以 -->
      <!-- <input type="checkbox" :checked="isAll" @change="checkAll"/> -->
      <input type="checkbox" v-model="isAll"/>
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
    props: ["todos","checkAllTodo","clearAllTodo"],
    computed: {
      isAll:{
        get(){
          return this.doneTotal === this.total && this.total>0
        },
        set(value){
          this.checkAllTodo(value)
        }
      },

      // 不用v-model可以这样写,但是用v-model:如果想能修改值,则必须写成上面getter,setter的形式
      /* isAll(){
        return this.doneTotal === this.total  && this.total>0
      }, */
      total(){
        return this.todos.length
      },
      doneTotal() {
        /* const x = this.todos.reduce((pre,current)=>{
          console.log("@",pre,current)
          return pre+(current.done ?1:0)
        },0) */
        return this.todos.reduce((pre, todo) => pre + (todo.done ? 1 : 0), 0)
      }
    },
    methods:{
      checkAll(e){
        // console.log(e.target.checked)
        this.checkAllTodo(e.target.checked)
      },
      clearAll(){
        this.clearAllTodo()
      }
    }
}
</script>

<style>
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