<template>
    <div>
        <input type="text" v-model="mytext">
        <p>{{mytext}}</p>
    </div>
</template>
<script>
    export default{
        data(){
            return{
                mytext :''
            }
        },
        methods :{
            // onclick(e){
            //     this.mytext=e.target.value;
            // }
        }
    }
</script>