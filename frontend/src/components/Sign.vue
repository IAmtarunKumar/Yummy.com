<template>
    <div id="loginDiv">

        <form @submit.prevent="registerUser">
            <h3>Sign In Here</h3>
            <label for="name">Username</label>
            <input type="text" placeholder="Enter Your Name" id="username" v-model="username" required>

            <label for="email">Email</label>
            <input type="email" placeholder="Email or Phone" id="email" v-model="email" required>

            <label for="password">Password</label>
            <input type="password" placeholder="Password" id="password" v-model="password" required>

            <button>Sign In</button>
            
            <br>
            <!-- <a style="text-decoration: none; color:rgb(18, 110, 147)" href="">I am already member</a> -->
            <br>
            <router-link style="text-decoration: none; border:1px solid rgb(50, 130, 67); padding:8px; background-color:rgb(7, 54, 24); color:white; border-radius:5px" to="/login">I am already member</router-link>
            
            
        </form>

        
    </div>
</template>
     
     
<script>


import axios from 'axios';
import Swal from 'sweetalert2';
export default {
    name: "SignInPage",

    data() {
        return {
            username: '',
            email: '',
            password: '',

        };
    },

    methods: {
        registerUser() {
            // Create an object with the user data
            const userData = {
                username: this.username,
                email: this.email,
                password: this.password,
            };

            axios.post('https://django-chack.onrender.com/register/', userData)
                .then((response) => {

                    if (response.data.message== 'User registered successfully') {
                        console.log('User registered successfully:', response.data);
                        Swal.fire({
                            position: 'center',
                            icon: 'success',
                            title: 'Sign In Successfully 🤗',
                            showConfirmButton: false,
                            timer: 1500
                        })
                        this.$router.push('/login');
                    }else{
                        Swal.fire({
                        icon: 'error',
                        title: 'Oops...',
                        text: 'Something went wrong! ☠️',
                        
                    })
                    }
                    // You can handle the response as needed
                })
                .catch((error) => {
                    console.error('Error registering user:', error);
                    Swal.fire({
                        icon: 'error',
                        title: 'Oops...',
                        text: 'Something went wrong! ☠️',
                       
                    })
                });
        }


    }
}



</script>
     
     
 
   
     
<style scoped>
#loginDiv {
    width: 100%;
    height: 98vh;
    background: url("../img/login_background.png");
  
    background-size: cover;
    background-repeat: no-repeat;
    background-attachment: fixed;
    background-position: center center;
    display: flex;
    justify-content: center;
    align-items: center;
    
  }
  
  form {
    height: 580px;
    width: 400px;
    background-color: rgba(21, 157, 62, 0.664);
   
   margin-top: 100px;
   margin-bottom: 100px;
    
    border-radius: 10px;
    backdrop-filter: blur(10px);
    border: 2px solid rgba(58, 237, 114, 0.1);
    box-shadow: 0 0 40px rgba(6, 54, 32, 0.6);
    padding: 50px 35px;
  }
  
  form * {
    font-family: "Poppins", sans-serif;
    color: #0c2b19;
    letter-spacing: 0.5px;
    outline: none;
    border: none;
  }
  
  form h3 {
    font-size: 32px;
    font-weight: 501;
    line-height: 42px;
    text-align: center;
  }
  
  label {
    display: block;
    margin-top: 30px;
    font-size: 16px;
    font-weight: 501;
  }
  
  input {
    display: block;
    height: 50px;
    width: 100%;
    background-color: rgba(227, 234, 229, 0.712);
    border-radius: 3px;
    padding: 0 10px;
    margin-top: 2px;
    font-size: 14px;
    font-weight: 300;
  }
  
  ::placeholder {
    color: #9eb4a6;
  }
  
  button {
    margin-top: 30px;
    width: 100%;
    background-color: #071207;
    color: #efeef5;
    padding: 15px 0;
    font-size: 18px;
    font-weight: 600;
    border-radius: 5px;
    cursor: pointer;
  }
  
  .social {
    margin-top: 30px;
    display: flex;
  }
  
  .social div {
    background: red;
    width: 150px;
    border-radius: 3px;
    padding: 5px 10px 10px 5px;
    background-color: rgba(255, 255, 255, 0.27);
    color: #eaf0fb;
    text-align: center;
  }
  
  .social div:hover {
    background-color: rgba(255, 255, 255, 0.47);
  }
  
  .social .fb {
    margin-left: 25px;
  }
  
  .social i {
    margin-right: 4px;
  }
  
  
  @media screen and (min-width: 200px) and (max-width: 400px) {
    form{
       height: 570px;
    width: 300px;
    background-color: rgba(21, 157, 62, 0.664);
   
   
    
    border-radius: 10px;
    backdrop-filter: blur(10px);
    border: 2px solid rgba(58, 237, 114, 0.1);
    box-shadow: 0 0 40px rgba(6, 54, 32, 0.6);
    padding: 50px 35px;
    }
    input {
      display: block;
      height: 50px;
      width: 100%;
      background-color: rgba(227, 234, 229, 0.712);
      border-radius: 3px;
      padding: 0 10px;
      margin-top: 2px;
      font-size: 14px;
      font-weight: 300;
    } 
       
      
     
      
  }
    /* Styles for screens between 769px and 1024px wide (Tablet) */
    @media screen and (min-width: 769px) and (max-width: 1024px) {
    
     
       
      
     
      
    }
    
    /* Styles for screens between 1025px and 1440px wide (Laptop) */
    @media screen and (min-width: 1025px) and (max-width: 1440px) {
    
      /* Add specific laptop styles here */
    }
    
    /* Styles for screens wider than 1440px (Extra Large) */
    @media screen and (min-width: 1441px) {
    
      /* Add specific extra-large screen styles here */
    }
    
    
  
  
</style>