<template>
  <div id="app">
    <TodoListContainer>
      <TodoListHeader
        :defaultInputValue="newItemText"
        @todoBtnClick="addTodo"
        @todoInput="nameTodo"
      />
      <TodoList>
        <transition-group name="fade" mode="out-it">
        <TodoListItem
          v-for="(item, index) in items"
          :key="index + 0"
          :text="item.text"
          :idx="index"
          :crossed="item.isDone"
          @todoItemState="todoItemState"
          @todoItemDelete="todoItemDelete"
        />
        </transition-group>
      </TodoList>
    </TodoListContainer>
  </div>
</template>

<script>
import TodoListContainer from './components/todo-list-container/todo-list-container.vue'
import TodoListHeader from './components/todo-list-header/todo-list-header.vue'
import TodoList from './components/todo-list/todo-list.vue'
import TodoListItem from './components/todo-list-item/todo-list-item.vue'

export default {
  name: 'App',
  components: {
    TodoListContainer,
    TodoListHeader,
    TodoList,
    TodoListItem
  },
  data() {
    return {
      items: [
        {
          text: 'Learn CSS',
          isDone: false,
        },
        {
          text: 'Learn HTML',
          isDone: false,
        },
        {
          text: 'Learn JavaScript',
          isDone: false,
        }
      ],
      newItemText: ''
    }
  },
  
  methods: {
    addTodo() {
      if (this.newItemText && this.newItemText.length > 0) {
          this.items.push({
          text: this.newItemText,
          isDone: false,
        });
      }
      this.newItemText = '';
    },
    nameTodo(text) {
      this.newItemText = text;
    },
    todoItemState(idx) {
      this.items[idx].isDone = !this.items[idx].isDone;
    },
    todoItemDelete(idx) {
      this.items.splice(idx, 1);
    },
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Roboto+Condensed');

#app {
  font-family: 'Roboto Condensed', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

html, body {
  font-family: 'Roboto Condensed', sans-serif;
  height:100%;
  min-height:100%; 
}

html, body, body div, span, object, iframe,
h1, h2, h3, h4, h5, h6, p, blockquote, pre,
abbr, address, cite, code, del, dfn, em,
img, ins, kbd, q, samp, small, strong,
sub, sup, var, b, i, dl, dt, dd, ol, ul,
li, fieldset, form, label, legend, table,
caption, tbody, tfoot, thead, tr, th, td,
article, aside, figure, footer, header, hgroup,
menu, nav, section, time, mark, audio, video {
  margin: 0;
  padding: 0;
  border: 0;
  outline: 0;
  font-size: 100%;
  vertical-align: baseline;
  background: transparent;
}
</style>
