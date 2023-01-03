<template>
    <img class="logo" src="../assets/resto-logo.jpg" />
    <h1>SignUp</h1>
    <div class="register">
        <input type="text" v-model="name" placeholder="Enter name"/>
        <input type="email" v-model="email"  placeholder="Enter Email"/>
        <input type="password" v-model="password"  placeholder="Enter Password"/>
        <button v-on:click="signUp">SignUp</button>
    </div>
</template>
<script>
import axios from 'axios'
export default{
    name:'SignUp',
    data(){
        return{
            name:'',
            email:'',
            password:''
        }
    },
    methods:{
       async signUp(){
            console.log(this.name,this.email,this.password)
            let result= await axios.post("http://localhost:3000/user",{
              name: this.name,
              email:this.email,
              password:this.password
            });
            console.log(result);
            if (result.status==201){
                alert("sign up done");
            }
            localStorage.setItem("user info",JSON.stringify(result.data))
        }
    }
}
</script>
<style>
.logo{
  width:100px;
 
 
}
.register input{
    margin-left: auto;
    margin-right: auto;
    width: 300px;
    height: 40px;
    margin-bottom: 30px;
    display: block;
    border: 1px solid skyblue;
    padding-left: 10px;
}
.register button{
width:320px;
height: 40px;
color: #fff;
background-color: skyblue;
border: 1px solid skyblue;
margin-left: auto;
margin-right: auto;
display: block;
cursor: pointer;

}

</style>