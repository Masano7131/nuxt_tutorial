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
      <label class="task-list__item"
             v-for="todo in todos">
        <input type="checkbox" v-model="todo.done"><button>EDIT</button>{{ todo.text }}
      </label>
    </div>
  </div>
</template>

<script>
export default {
  name: 'hello',
  data:  () => {
    return {
      msg: 'やることリスト',
      todos : [],
      newTodo: ""
    }
  },
  methods: {
    addTodo: function(event) {
      let text = this.newTodo && this.newTodo.trim()
      if (!text) {
        return
      }
      this.todos.push({
        text: text,
        done: false
      })
      this.newTodo = ''
    },
    removeTodo: function(event){
      for (let i = this.todos.length - 1; i >= 0; i--) {
        if (this.todos[i].done) this.todos.splice(i, 1)
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
@mixin flex-vender() {
  display: flex;
  display: -webkit-flex;
  display: -moz-flex;
  display: -ms-flex;
  display: -o-flex;
}
.task-list {
  @include flex-vender;
  flex-direction: column;
  align-items: center;
  &__item {
    width: 270px;
    text-align: left;
    $element: #{&};
    &--checked {
      @extend #{$element};
      color: #85a6c6;
    }
  }
}
</style>