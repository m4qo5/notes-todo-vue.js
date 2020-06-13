<template>
    <a
        class="custom-span-button"
        v-on="$listeners"
        v-bind="$attrs"
    >
        {{ text }}
    </a>
</template>

<script>
export default {
    name: "TodoListBaseButton",
    props: {
        text: {
            type: String,
            default: 'Add'
        }
    }
}
</script>


<style scoped>
.custom-span-button {
  width: 25%;
  display: inline-block;
  padding: 1em 1em;
  text-decoration: none;
  background: #f7f7f7;
  border-right: 3px solid black;
  margin: 0.25em;
  color: black;
  font-size: 16px;
  font-weight: bold;
  cursor: pointer;
  transition: 0.2s;
}

.custom-span-button:active {
  box-shadow: inset 0 0 2px rgba(128, 128, 128, 0.1);
  transform: translateY(12px);
}

.custom-span-button:hover {
  background: #ddd;
}
</style>