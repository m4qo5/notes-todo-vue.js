<template>
    <div class="todo-list-header-container">
        <h1 
            v-text="todoListTitle"
            class="todo-list-header-heading"
        />
        <div class="control-container">
            <TodoListBaseInput 
                :placeholder="todoItemInputPlaceholder"
                :value="defaultInputValue"
                @input="emitTodoInput"
            />
            <TodoListBaseButton
                @click="emitTodoBtnClick"
            />
        </div>
    </div>
</template>


<script>
import TodoListBaseInput from '../generic/base-input/todo-list-base-input.vue'
import TodoListBaseButton from '../generic/base-button/todo-list-base-button.vue'

export default {
    name: 'TodoListHeader',
    components: {
        TodoListBaseInput,
        TodoListBaseButton
    },
    data() {
        return {
            todoListTitle: 'My Notes',
            todoItemInputPlaceholder: 'Title...',
        }
    },
    props: {
        defaultInputValue: {
            type: String,
            default: ''
        }
    },
    methods: {
        emitTodoBtnClick() {
            this.$emit('todoBtnClick');
        },
        emitTodoInput(text) {
            this.$emit('todoInput', text);
        }
    }
}
</script>


<style scoped>
.todo-list-header-container {
  text-align: center;
  font-size: 21px;
  font-weight: 100;
  padding: 20px 40px;
  text-align: center;
}

.todo-list-header-heading {
  margin-bottom: 14px;
}

.control-container {
  display: flex;
  flex-direction: row;
}
</style>