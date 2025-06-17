<script setup>
import axios from 'axios';
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
</script>

<template>
  <div class="form-container">
    <form @submit.prevent="Submit">
      <h2 class="form-title">Form user</h2>
      
      <div class="form-group">
        <label for="username">Username</label>
        <input 
          type="text" 
          id="username"
          v-model="username"
          placeholder="Enter your username" 
          required
        >
      </div>
      
      <div class="form-group">
        <label for="password">Password</label>
        <input 
          type="password" 
          id="password"
          v-model="password"
          placeholder="Enter your password" 
          required
        >
      </div>
      
      <button type="submit" class="submit-btn">Submit</button>
    </form>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  data() {
    return {
      username: '',
      password: ''
    }
  },
  methods: {
    Submit() {
      try{
        axios.post("http://localhost:8080/api/me",{
          username:this.username,
          password:this.password
        })
      }catch(error){
        console.error("There was an error sunmitting form!",error);
      }
      // console.log('Username:', this.username);
      // console.log('Password:', this.password);
      // Add your form submission logic here
    }
  }
}
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.form-container {
  background-color: #f5f5f5;
  padding: 30px;
  border-radius: 8px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
  width: 300px;
  margin: 50px auto;
}

.form-title {
  text-align: center;
  margin-bottom: 25px;
  color: #333;
  font-size: 18px;
  font-weight: normal;
}

.form-group {
  margin-bottom: 15px;
}

label {
  display: block;
  margin-bottom: 5px;
  color: #666;
  font-size: 14px;
}

input[type="text"],
input[type="password"] {
  width: 100%;
  padding: 12px;
  border: 1px solid #ddd;
  border-radius: 4px;
  font-size: 14px;
  background-color: #fff;
  transition: border-color 0.3s ease;
}

input[type="text"]:focus,
input[type="password"]:focus {
  outline: none;
  border-color: #4CAF50;
}

input[type="password"] {
  background-color: #4a4a4a;
  color: white;
  border: 1px solid #666;
}

input[type="password"]::placeholder {
  color: #aaa;
}

.submit-btn {
  width: 100%;
  padding: 12px;
  background-color: #4CAF50;
  color: white;
  border: none;
  border-radius: 4px;
  font-size: 16px;
  cursor: pointer;
  transition: background-color 0.3s ease;
  margin-top: 10px;
}

.submit-btn:hover {
  background-color: #45a049;
}

.submit-btn:active {
  background-color: #3d8b40;
}
</style>