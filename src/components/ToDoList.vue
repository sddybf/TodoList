<template>
    <div class="todo">
        <h2 class="ViceTitle">ToDo<span class="count">{{doinglist.length}}</span></h2>
        <ol class="box">
            <TodoItem v-for="item in doinglist" :key="item.id" :todoitem="item" :checkDone='checkDone' :remove="remove"></TodoItem>
        </ol>
    </div>
</template>

<script>
import TodoItem from './TodoItem'

export default {
    name: 'ToDoList',
    components:{
        TodoItem
    },

    props: ['todos', 'remove'],

    computed: {
        doinglist(){
            return this.todos.filter(function(todoitem){
                return !todoitem.done
            })
        }
    },
    
    methods: {
        checkDone(item){
            // this.$set(this.todos, ind, {...this.todos[ind], done: true})
            item.done = true
        }
    },
}

</script>

<style scoped>
.ViceTitle{
    text-align: center;
}

.todo{
    width: 50%;
    height: 500px;
    background-color: indianred;
    float: left;
    margin-left: 0;
    margin-top: 0px;
}

.count{
    background-color: darkgray;
    color: rgb(32, 54, 178);
    border-radius: 50%;
    line-height: 25px;
    width: 25px;
    height: 25px;
    display: inline-block;
}

.box{
    /* text-align:center;  */
    text-align:left;
}
</style>