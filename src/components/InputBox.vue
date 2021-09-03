<template>
    <div class="making">
        What to do: 
        <input @keyup.enter.prevent="Add" v-model="title"/>
        <button @click.prevent="Add">Add</button>
    </div>
</template>

<script>
import {nanoid} from 'nanoid'

export default {
    name: 'InputBox',
    props: ['addTodo'],
    data() {
        return {
            title: ''
        }
    },
    
    methods: {
        Add(){
            if (!this.title.trim()) {
                return alert('输入不能为空')
            }
            else {
                const todoitem = {id: nanoid(), title: this.title, done: false}
                this.addTodo(todoitem)
                this.title = ''
            }
        }
    },
}
</script>

<style scoped>
.making{
    width: 100%;
    height: 40%;
    background-color: honeydew;
    margin: 0 auto;
    text-align: center;
}
</style>