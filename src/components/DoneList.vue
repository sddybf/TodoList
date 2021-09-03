<template>
    <div class="done">
        <h2 class="ViceTitle">ToDo<span class="count">{{donelist.length}}</span></h2>
        <ol class="box">
            <DoneItem v-for="item in donelist" :key="item.id" :doneitem="item" :checkTodo="checkTodo" :remove="remove"></DoneItem>
        </ol>
    </div>
</template>

<script>
import DoneItem from './DoneItem'

export default {
    name: 'DoneList',
    components:{
        DoneItem
    },

    props: ['todos', 'remove'],

    computed: {
        donelist(){
            return this.todos.filter(function(todoitem){
                return todoitem.done
            })
        },
    },
    
    methods: {
        checkTodo(item){
            item.done = false
        }
    },
}
</script>

<style scoped>
.ViceTitle{
    text-align: center;
}

.done{
    width: 50%;
    height: 500px;
    background-color: chartreuse;
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