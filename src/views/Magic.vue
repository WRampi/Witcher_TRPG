<script setup lang="ts">
import { ref } from 'vue';

let users=ref<any>([]);
const request = new XMLHttpRequest();
request.open("GET", "magic.json", true);
request.onload = function () {
	users.value = JSON.parse(this.response);
};
request.send();

function click(){
  
  const request = new XMLHttpRequest();
  request.open("POST", "magic.json", false);
  request.send(JSON.stringify(users.value));  
}

</script>

<template>
  <ul>
    <li v-for="user in users">
      <h1><label class="label label-info">TestText</label></h1><br>      
      <input type="text" v-model="user.text" placeholder="TestText" class="form-control" /><br>
      <h1><label class="label label-info">TestPassword</label></h1><br>
      <input type="password" v-model="user.password" placeholder="TestPassword" class="form-control" /><br>
      <h1><label class="label label-info">TestNumber</label></h1><br>
      <input type="number" v-model="user.number" min="0" placeholder="TestNumber" class="form-control" /><br>
      <h1><label class="label label-info">TestDate</label></h1><br>   
      <input type="date" v-model="user.date" placeholder="TestDate" class="form-control" />
      <h1><label class="label label-info">TestTextArea</label></h1><br> 
      <textarea v-model="user.textarea" placeholder="TestTextArea" class="form-control" /><br>
      <div>
        <p style="white-space: pre-line">{{user.textarea}}</p>
      </div>
    </li>
  </ul>

  <button @click="click" class="btn btn-lg btn-default">Save</button>

  <input type="file" accept="application/json" @change="onFileChange">

</template>
