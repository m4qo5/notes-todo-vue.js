<template>
    <transition name="fade" mode="out-in">
        <li 
            class="todo-list-item"
            :class="{crossed: crossed}"
        >
            {{ text }}
            <div>
                <transition name="fade" mode="out-in">
                    <font-awesome-icon
                        v-if="!crossed"
                        :icon="['fa', 'check-circle']"
                        key="check-logo"
                        @click="emitTodoItemState"
                    />
                    <font-awesome-icon
                        v-else
                        :icon="['fa', 'minus-circle']"
                        key="minus-logo"
                        @click="emitTodoItemState"
                    />
                </transition>
                <font-awesome-icon
                    :icon="['fa', 'trash']"
                    @click="emitTodoItemDelete"
                />
            </div>
        </li>
    </transition>
</template>


<script>
export default {
    name: 'TodoListItem',
    props: {
        text: {
            type: String,
            default: 'default task'
        },
        idx: {
            type: Number,
        },
        crossed: {
            type: Boolean,
            default: false
        }
    },
    methods: {
        emitTodoItemState() {
            this.$emit('todoItemState', this.idx)
        },
        emitTodoItemDelete() {
            this.$emit('todoItemDelete', this.idx)
        },
    }
}
</script>


<style scoped>
.todo-list-item {
  position: relative;
  padding: 12px;
  margin-bottom: 12px;
  background: whitesmoke;
  font-size: 16px;
  transition: 0.4s;
  font-weight: 100;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
  border: 6px solid #eee;
  border-right: 3px solid black;
  border-left: 3px solid black;
  text-align: start;
  display: flex;
  justify-content: space-between;
}

.todo-list-item:hover {
  background: #ddd;
}

svg {
  cursor: pointer;
  margin-left: 8px;
}

.crossed {
  text-decoration: line-through;
  transition: text-decoration .4s
}

.fade-enter-active, .fade-leave-active {
    transition: opacity .4s
}
.fade-enter, .fade-leave-to /* .fade-leave-active in <2.1.8 */ {
    opacity: 0
}
</style>