<template>
    <form @submit.prevent="onSubmit">
        <label for="todo-input">Mitä pitäisi tehdä?</label>
        <input 
            type="text"
            id="todo-input"
            name="new-todo"
            autocomplete="off"
            v-model.lazy.trim="label"  />
        <button type="submit">Lisää</button>
    </form>
</template>

<script>
    export default {
        methods: {
            onSubmit() {
                if (this.label === "") {
                    return
                }
                this.$emit("todo-added", this.label)
                this.label = ""
            }
        },
        data () {
            return {
                label: ""
            }
        }
    };
</script>