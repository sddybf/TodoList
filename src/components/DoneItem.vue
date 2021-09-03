<template>
    <li>
        <!-- <input type="text"> -->
        <input type="checkbox" :checked="checkChecked" @click.prevent="handleCheckTodo(doneitem)">
        <label> {{doneitem.title}} </label>
        <a @click.prevent="handleRemove(doneitem.id)">-</a>
    </li>
</template>

<script>
export default {
    name: 'DoneItem',
    props:['doneitem', 'checkTodo', 'remove'],
    computed:{
        checkChecked(){
            return this.doneitem.done ? this.doneitem.done : ''
        }
    },

    methods: {
        handleCheckTodo(item){
            this.checkTodo(item)
        },

        handleRemove(id){
            if (confirm('确定删除吗？')) {
                this.remove(id)
            }
        }
    },
}

</script>

<style>

</style>