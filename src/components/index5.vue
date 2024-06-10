<template>
    <div>
        <input type="text" v-model="oninput">
        <p>{{oninput}}</p>
    </div>
</template>
<script>
    export default{
        data(){
            return{
                oninput: ""
            }
        },
        methods :{

        }
    }
</script>
