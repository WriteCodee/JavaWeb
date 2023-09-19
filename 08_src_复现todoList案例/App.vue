<template>
  <div id="root">
    <div class="todo-container">
      <div class="todo-wrap">
        <MyHeader :addTodo="addTodo" />
        <MyList :todoList="todoList" :checkTodo="checkTodo" :deleteTodo="deleteTodo" />
        <MyFooter :todoList="todoList" :checkAllTodo="checkAllTodo" :deleteAllTodo="deleteAllTodo"/>
      </div>
    </div>
  </div>
</template>

<script>
import MyHeader from "./components/MyHeader.vue";
import MyList from "./components/MyList.vue"
import MyFooter from "./components/MyFooter.vue"
export default {
  name: "App",
  components: { MyHeader, MyList, MyFooter },
  data() {
    return {
      todoList: [
        { id: "001", title: "Vue", done: true },
        { id: "002", title: "Web", done: false },
        { id: "003", title: "Java", done: true },
      ]
    }
  },
  methods: {
    // 添加一个todo
    addTodo(x) {
      this.todoList.unshift(x)
    },
    // 勾选or取消勾选一个头都
    checkTodo(id) {
      this.todoList.forEach((todo) => {
        if (todo.id === id) todo.done = !todo.done
      })
    },
    // 删除一个Todo
    deleteTodo(id) {
      this.todoList = this.todoList.filter((todo) => {
        return todo.id !== id
      })
    },
    // 全选or全不选
    checkAllTodo(done){
      this.todoList.forEach((todo)=>{
        return todo.done = done
      })
    },
    // 清楚所有已完成的
    deleteAllTodo(){
      this.todoList = this.todoList.filter((todo)=>{
        return !todo.done
      })
    }
  }


}
</script>

<style>
/*base*/
body {
  background: #fff;
}

.btn {
  display: inline-block;
  padding: 4px 12px;
  margin-bottom: 0;
  font-size: 14px;
  line-height: 20px;
  text-align: center;
  vertical-align: middle;
  cursor: pointer;
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.2), 0 1px 2px rgba(0, 0, 0, 0.05);
  border-radius: 4px;
}

.btn-danger {
  color: #fff;
  background-color: #da4f49;
  border: 1px solid #bd362f;
}

.btn-danger:hover {
  color: #fff;
  background-color: #bd362f;
}

.btn:focus {
  outline: none;
}

.todo-container {
  width: 600px;
  margin: 0 auto;
}

.todo-container .todo-wrap {
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
}
</style>