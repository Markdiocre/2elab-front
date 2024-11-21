<script setup>
import NavBar from '@/components/NavBar.vue';
import axios from 'axios'

function makeRequest(){
  console.log("Clicked")

  axios.get("http://localhost:3000/users/",{
    // headers:{
    //   Authorization: "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjEyMzIxMzEyMzEyMzEyMzEyMDAwLCJpZCI6MiwibmFtZSI6Im1hcmsiLCJpYXQiOjE3MzA5ODMyNTN9.rVpKYDCXSea7DugMpbYs6dti9T6DiTJjmY7wIJJGLig"
    // }

    headers:{
      Authorization: "Bearer "+localStorage.getItem('token')
    }
  })
  .then((res)=>{
    localStorage.setItem('token', res.data.token)
    console.log(res.data)
  })
  .catch((err)=>{
    console.log(err.message)
  })
}



</script>

<template>
  <NavBar/>

  <button @click="makeRequest">Make an api request</button>
  Hellooo
</template>

<style scoped>

</style>
