<template>
    <div class="todo-list">
        <ol>
            <slot></slot>
        </ol>
    </div>
</template>


<script>
export default {
    name: 'TodoList',
}
</script>


<style scoped>
.todo-list {
  text-align: center;
  font-size: 21px;
  font-weight: 100;
  padding: 30px 40px;
  text-align: center;
}

ol {
  margin-left: 0.4em;
  margin-right: 0.15em;
  list-style: none;
}
</style>