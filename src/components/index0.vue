<template>
    <div>   
        <header class="head">
            <div class="image">
                <img src="../assets/logo.svg" alt="">
            </div>
            <div>
                <ul>
                    <li>Home</li>
                    <li><button @click="handleadduser">Add User</button></li>
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
            <form v-if="isVisibleadd" class="myform" @submit.prevent="handleadd">
              <h2 class="text">Form for Add User</h2>
              <div>
                  <label for="id">ID :</label>
                  <input type="number" name="id" v-model="inputValue.ID">
              </div>
              <div>
                  <label for="name">Name :</label>
                  <input type="text" name="name" v-model="inputValue.Name">
              </div>
              <div>
                  <label for="email">Email :</label>
                  <input type="email" name="email" v-model="inputValue.Email">
              </div>
              <div class="btn">
                  <button type="submit">Submit</button>
                  <button type="button" @click="handleadduser">Close</button>
              </div>
          </form>



            <form v-if="isVisible" class="myform" @submit.prevent="handleChange">
                <h2 class="text">Form for Edit</h2>
                <div>
                    <label for="id">ID :</label>
                    <input type="number" name="id" v-model="inputValue.ID">
                </div>
                <div>
                    <label for="name">Name :</label>
                    <input type="text" name="name" v-model="inputValue.Name">
                </div>
                <div>
                    <label for="email">Email :</label>
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
              isVisibleadd : false,
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
          handleadduser(){
            this.isVisibleadd = !this.isVisibleadd;
          },
          handleadd (){
            this.isVisibleadd = !this.isVisibleadd;
            this.myInfo.push({...this.inputValue});
          },
          Close(){
            this.isVisible =! this.isVisible;
          },
          handleDelete(index){
            this.myInfo.splice(index, 1);
          }
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
  li{
    display: grid;
    text-decoration: none;
  }
  li button{
    cursor: pointer;
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
  .text{
    font-weight: bold;
    font-size: 30px;
    text-align: center;
    color:black;
  }
  form{
    padding: 20px 20px;
    width: 500px;
    height: 250px;
    background-color:rgb(248, 199, 224);
    border-radius: 10px;
    position: absolute;
    margin-bottom: 420px;
  }
  form label{
    font-weight: bold;
    width: 300px;
    font-size: 30px;
    margin-left: 50px;
  }
  form input{
    width: 300px;
    height: 30px;
    cursor: pointer;
  }
  .btn{
    display: flex;
    justify-content: center;
  }
  form button:nth-child(1){
    margin-top: 20px;
    width: 65px;
    height: 30px;
    margin-left: 10px;
    background-color: greenyellow;
    font-size: 15px;
    font-weight: bold;
    border-radius: 5px;
  }
  form button:nth-child(2){
    margin-top: 20px;
    width: 60px;
    height: 30px;
    margin-left: 10px;
    background-color:red;
    font-size: 15px;
    font-weight: bold;
    border-radius: 5px;
  }

   
</style>