<template>
    <div>   
        <header class="head">
            <div class="image">
                <img src="../assets/logo.svg" alt="">
            </div>
            <div>
                <ul>
                    <li>Home</li>
                    <li>Add User</li>
                </ul>
            </div>
        </header>
        <main>
            <table>
                <tr>
                    <th>S/N</th>
                    <th>UserName</th>
                    <th>Email</th>
                    <th>Edit</th>
                    <th>Delete</th>
                </tr>
                <tr v-for="(myinfo, key) in myInfo" :key="key">
                    <td>{{myinfo.ID}}</td>
                    <td>{{myinfo.Name}}</td>
                    <td>{{myinfo.Email}}</td>
                    <td>
                        <span @click="handleEdit(key)">Edit</span>
                    </td>
                    <td>
                        <span @click="handleDelete(key)">Delete</span>
                    </td>
                </tr>
            </table>
            <form v-if="isVisible" class="myform" @submit.prevent="handleChnage">
                <h2 class="font-bold text-4xl text-yellow-300 text-center">Form for Edit</h2>
                <div>
                    <label for="id">ID</label>
                    <input type="number" name="id" v-model="inputValue.ID">
                </div>
                <div>
                    <label for="name">Name</label>
                    <input type="text" name="name" v-model="inputValue.Name">
                </div>
                <div>
                    <label for="email">Email</label>
                    <input type="email" name="email" v-model="inputValue.Email">
                </div>
                <div class="btn">
                    <button type="submit">Submit</button>
                    <button type="button" @click="Close">Close</button>
                </div>
            </form>
        </main>
    </div>
</template>
<script>
    export default {
        data(){
            return{
              isVisible : false,
              myIndexKey: 0,
                inputValue :{
                    ID:0,
                    Name:"",
                    Email:"",
                },
                myInfo :[
                  {
                    ID: 1,
                    Name: "Kaka",
                    Email: "KampongCham Province",
                  },
                  {
                    ID: 2,
                    Name: 'panha',
                    Email: 'kandal Province',
                  },
                  {
                    ID:3,
                    Name: 'kak sruoch',
                    Email: 'PreyVeng Province',
                  },
                ]
            }
        },
        methods : {
          handleEdit(index){
            this.myIndexKey= index;
            this.isVisible = !this.isVisible;
            this.inputValue.ID = this.myInfo[index].ID;
            this.inputValue.Name = this.myInfo[index].Name;
            this.inputValue.Email = this.myInfo[index].Email;
          },
          handleChange() { 
            this.isVisible = !this.isVisible;
            this.myInfo[this.myIndexKey].ID = this.inputValue.ID;
            this.myInfo[this.myIndexKey].Name = this.inputValue.Name;
            this.myInfo[this.myIndexKey].Email = this.inputValue.Email;
          },
          Close(){
            this.isVisible =! this.isVisible;
          },
        }
    }
</script>
<style>
main{
    display: flex;
    flex-flow: column;
    justify-content: center;
    align-items: center;
    height: 90vh;
  }
  .head     {
    padding-top: 10px;
    padding-bottom: 10px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding-inline: 10px;
    background-color: chocolate;
  }
  .imgDiv{
    width: 40px;
  }
  ul{
    display: flex;
    gap: 10px;
    font-weight: bolder;
  }
  th {
    color: white;
  }
  td, th{
    padding: 20px 40px;
  }
  tr:nth-child(even){
    background-color: rgba(128, 128, 128, 0.685);
  }
  tr:nth-child(odd) td:nth-child(even){
    background-color: rgba(141, 143, 142, 0.317);
  }
  tr:nth-child(1){
    background-color: rgb(71, 69, 69);
  }
  td:nth-child(4) span{
    background-color: yellow;
    padding: 10px 20px;
    border-radius: 5px;
    font-weight: bold;
    cursor: pointer;
  }
  td:nth-child(5) span{
    padding : 10px 20px;
    background-color: red;
    color : white;
    border-radius: 5px;
    font-weight: bold;
    cursor: pointer;
  }
  li:hover{
    cursor: pointer;
    color: blue;
  }
  form{
    width: 900px;
    height: 300px;
    align-items: center;
    gap:10px;
    display: flex;
    justify-content:center;
    margin-top: 10px;
    padding-top: 30px;
    flex-flow: column;
    background-color: rgb(206, 199, 199);
    border-radius: 10px;
    position: absolute;
  }
  form div{
    display: flex;
    justify-content: center;
    align-items: center;
  }
  form div:nth-child(2){
    gap: 30px;
  }
  form div:nth-child(3){
    gap: 30px;
  } form div:nth-child(4){
    gap: 30px;
  }
  label{
    text-align: end;
    width: 10%;
    font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
    font-weight: bold;
    margin-right: 10px;
  }
  input{
    width: 700px;
    height: 20px;
  } 
  form div:nth-child(5) button:nth-child(1){
    color : black;
    background-color: greenyellow;
  }
  form div:nth-child(5) button:nth-child(2){
    color: back;
    background-color: red;
  }
  .btn,button:nth-child(1){
    gap: 20px;
    width: 100px;
    height: 30px;
    border-radius: 5px;
  }
  .btn,button:nth-child(2){
    width: 100px;
    height: 30px;
    border-radius: 5px;
  }
</style>