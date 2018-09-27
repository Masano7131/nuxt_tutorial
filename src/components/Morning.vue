<template>
  <div>
    {{ msg }}
    <form>
      <button v-on:click="addTodo()">追加</button> 
      <button @click="removeTodo()">消す</button>
      <p>input: <input type="text" v-model="newTodo"></p>
      <p>task: {{ newTodo }}</p>
    </form>
    <div class="task-list">
      <label class="task-list__item" v-for="todo in todos">
        <input type="checkbox" v-model="todo.done"><button>EDIT</button>{{ todo.text }}
      </label>
    </div>
  </div>
</template>