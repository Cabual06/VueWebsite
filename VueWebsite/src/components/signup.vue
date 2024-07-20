<template>
    <div class="box-wrapper">
        <h1>SignUp</h1>
        <img class="logo" src="../assets/food.png" alt="">
        <div class="wrapper">
            <input type="text" v-model="name" placeholder="Enter your Name">
            <input type="text" v-model="email" placeholder="Enter your Email">
            <input type="password" v-model="password" placeholder="Enter your Password">
            <button v-on:click="signup">SignUp</button>
        </div>
    </div>
</template>

<script>
import axios from 'axios'
    export default {
        name: "signup",
        data(){
            return {
                name: "",
                email: "",
                password: "",
            }
        },

        methods:{
            async signup(){
                let result = await axios.post("http://localhost:3000/users",{
                    email: this.email,
                    password: this.password,
                    name: this.name
                });

                console.warn(result);
                if(result.status=201){
                    localStorage.setItem("users", JSON.stringify(result.data))
                }
            }
        }
    }
</script>

<style>

.box-wrapper{
    justify-content: center;
    align-items: center;
    width: 22%;
    display: flex;
    flex-direction: column;
    margin-left: auto;
    margin-right: auto;
    margin-top: 120px;
    padding-bottom: 30px;
}
.logo{
    width: 300px;
}

.wrapper input{
    width: 300px;
    height: 40px;
    padding-left: 20px;
    display: block;
    margin-bottom: 10px;
}

button{
    height: 40px;
    width: 100%;
}
</style>