<template>
    <div class="todo-list-background">
        <div class="todo-list-container">
            <slot></slot>
        </div>
    </div>
</template>


<script>
export default {
    name: 'TodoListContainer',
}
</script>


<style scoped>
.todo-list-background {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
  min-height: 100vh;
  min-width: 100vh;
  background: cornsilk;
}

.todo-list-container {
  background: white;
  overflow-y: auto;
  overflow-x: hidden;
  display: flex;
  flex-direction: column;
  min-width: 600px;
  min-height: 400px;
  border: 4px dotted #eee;
}
</style>