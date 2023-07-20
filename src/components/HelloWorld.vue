<template >
  <div class="main" >

    <div class="title">
      <h1>Vue to do list</h1>
    </div>
    <div class="controls-box">
      <input id="todo-input" type="text" class="todo-controls" v-model="inputTodo" placeholder="enter your todo!">
      <button type="submit" class="todo-controls" @click="addTodo(inputTodo)">
        Add
      </button>

      <button id="clear" class="todo-controls" @click="addTodo(inputTodo)">
        Clear
      </button>
    </div>
    <div class="todo-box">
      <div v-for="item in todoList" v-bind:key="item" class="todo-item">
          {{ item }}
          <button type="submit" class="todo-controls" @click="deleteTodo(item)">
        Delete
      </button>
      </div>
    </div>
    
  </div>
</template>
<script setup>
import { ref } from 'vue'

let todoList = ref(["shopping", "cooking"])

let addTodo = (inputTodo) => {
  if (todoList.value.length < 20) {
    todoList.value.push(inputTodo)
  } else {
    console.log("to much to todos!")
  }
}

let deleteTodo = (item) => {
  const index = todoList.value.indexOf(item)
    if (index > -1) { 
      todoList.value.splice(index, 1)
    }
}

</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.controls-box {
  background-color: antiquewhite;
  display: flex;
  flex-direction: row;
  justify-content: center;

}

.todo-controls {
  background-color: rgb(215, 234, 250);
  border: 1px solid grey;
  margin: 2px 2px 2px 2px;
}

#todo-input {
  width: 20vw;
}

#clear {
  margin-left: 60px;
}

.todo-box {
  width: 40vw;
  background-color: rgb(163, 211, 169);
  padding: 5vw;
}
.todo-item {
  background-color: rgb(163, 211, 196);
  border: 1px solid rgb(255, 255, 255);
  padding: 5px;
  margin: 5px;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}

</style>
