<template>
   <div class="row roomForm">
       <form class="form-inline" @submit.prevent="createNewRoom(room_name)">
           <div class="form-group mb-2">
               <input type="text" class="form-control" v-model="room_name" >
           </div>
           <button type="submit" class="btn btn-primary mb-2 createRoomBotton">Create Room</button>
       </form>
   </div>
</template>

<script>
import { EventBus } from '../Event'

export default {
 name: "AddRoom", // Component name
 data() {
   return {
    room_name: "",
   }
 },
 methods: {
   createNewRoom(name) {
       if(!name) {
         alert("please provide a room name");
         return
       }

       this.room_name = '';
       EventBus.$emit('new_room', name);
   }
 }
}
</script>

<style>
 .roomForm {
     margin-left: auto;
     margin-right: auto;
     margin-top: 30px;
     width: 100%;
 }
 .createRoomBotton {
   color: #fff;
   background-color: #4d555f;
   border-color: #303840;
   padding: 8px;
   font-weight: bolder;
 }
</style>