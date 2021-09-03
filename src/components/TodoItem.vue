<template>
    <li>
        <input type="checkbox" :checked="checkUnchecked" @click.prevent="handleCheckDone(todoitem)">
        <label> {{todoitem.title}} </label>
        <a @click.prevent="handleRemove(todoitem.id)">-</a>
    </li>
</template>

<script>
export default {
    name: 'TodoItem',
    props:['todoitem', 'checkDone', 'remove'],
    computed:{
        checkUnchecked(){
            return this.todoitem.done? this.todoitem.done : ''
        }
    },

    methods: {
        handleCheckDone(item){
            this.checkDone(item)
        },

        handleRemove(id){
            if (confirm("确定删除吗？")) {
                this.remove(id)
            }
        }
    },
}

</script>

<style>

</style>