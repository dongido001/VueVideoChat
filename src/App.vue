<template>
 <div class="container-fluid chat_container" id="app">
     <div class="row" v-if="authenticated">
       <Rooms />
       <Video :username="username"/>
       <Logs />
     </div>
     <div class="row" v-else>
       <div class="username">
           <form class="form-inline" @submit.prevent="submitUsername(username)">
             <div class="form-group mb-2">
                 <input type="text" class="form-control" v-model="username" >
             </div>
             <button type="submit" class="btn btn-primary mb-2 Botton">Enter!</button>
         </form>
       </div>
     </div>
 </div>
</template>

// ...

<script>
// import components
import Rooms from './components/Rooms'
import Video from './components/Video'
import Logs from './components/Logs'
import AddRoom from './components/AddRoom'

export default {
 name: 'App',
 data() {
   return {
     username: "",
     authenticated: false
   }
 },
 components: {
   Rooms,
   Video,
   Logs,
   AddRoom
 },
 methods: {
   submitUsername(username) {
      if(!username) {
        return alert('please provide a username');
      }

      this.authenticated = true;
   }
 }
 }
</script>

<style>
 #app {
   font-family: 'Avenir', Helvetica, Arial, sans-serif;
   -webkit-font-smoothing: antialiased;
   -moz-osx-font-smoothing: grayscale;
   text-align: center;
   color: #2c3e50;
   margin-top: 60px;
   background: #2c3e50;
 }
 .box {
   border: 1px solid gray;
 }

 .username {
   margin: 12px auto 7px auto;
   color: wheat;
 }

   .Botton {
   color: #fff;
   background-color: #4d555f;
   border-color: #303840;
   padding: 8px;
   font-weight: bolder;
 }
</style>