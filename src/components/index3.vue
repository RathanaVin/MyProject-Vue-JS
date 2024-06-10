<template>
    <div>
        <h1 :class="mystyle">{{mytitle}}</h1>
        <button @click="handelColors">Click Me</button>
    </div>
</template>
<script>
export default{
    data(){
        return{
            mystyle: 'red',
            mytitle : 'Hello everyone',
            mystatus : true
        }
    },
    methods: {
        handelColors (){
            if(this.mystatus==true){
                this.mystyle='blue';
                this.mystatus=! this.mystatus;
            }
            else{
                this.mystyle='red';
                this.mystatus=! this.mystatus;
            }
        }
    },
}
</script>
<style>
.red{
    font-weight: bold;
    color: red;
}
.blue{
    font-weight: bold;
    color: blue;
}
</style>