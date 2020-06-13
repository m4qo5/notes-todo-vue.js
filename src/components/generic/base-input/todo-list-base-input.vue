<template>
    <input
        class="todo-item-input"
        v-bind="$attrs"
        v-on="inputListeners"
    >
</template>


<script>
export default {
    name: 'TodoListBaseInput',
    computed: {
        inputListeners: function () {
            var vm = this
            return Object.assign({}, this.$listeners,
                        {
                    input: function (event) {
                        vm.$emit('input', event.target.value)  // make v-model work on component
                    }
                }
            )
        }
    },
}
</script>


<style scoped>
.todo-item-input {
    margin: 0;
    border: 1px solid cornsilk;
    border-radius: 0;
    width: 75%;
    padding: 10px;
    font-size: 16px;
    box-shadow: 0px 0px 0px 3px cornsilk;
    transition: box-shadow 0.4s linear;
    margin: 0.5em;
}

input:focus{
    outline: none;
    box-shadow: 0px 0px 0px 3px black;
}
</style>