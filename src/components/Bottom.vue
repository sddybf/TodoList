<template>
    <div class="Bottom">
        <button id="clearbutton" @click.prevent="clearAll"><Button>我不干了</Button></button>
    </div>
</template>

<script>
import Button from './Button.vue'
export default {
    name: 'Bottom',
    components: {
        Button
    },
    props: ['clear'],
    methods: {
        clearAll(){
            this.clear()
        }
    },
}
</script>

<style scoped>
.Bottom{
    width: 100%;
    height: 60px;
    background-color: black;
    margin: 0 auto;
    margin-top: 500px;
    text-align: center;
}
</style>