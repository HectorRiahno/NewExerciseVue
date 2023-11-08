<script setup>
import { ref } from 'vue';

  let nuevatarea  = ref("");
  let array = ref([{text : "estudiar", done:false},
                   {text : "fornite" , done:true }]);

  function addtarea(){
    if(nuevatarea.value.trim()==='')return

    array.value.push({text :nuevatarea.value , done: false})
    nuevatarea.value=''
  }
  function setDone(index){
    // if(array.value[index].done == false){
    //   array.value[index].done = true
    // }
    // if(array.value[index].done == true){
    //   array.value[index].done = false
    // }
    array.value[index].done = !array.value[index].done 
    
  }
  function eliminartarea(index){
    array.value.splice(index,1)
  }
</script>

<template>
  <div class="card">
    <h1>lista de cosas</h1>
    <p class="subtitulo">{{nuevatarea}}</p>
    <div>
      <div v-for="(tarea,index) in array" :key='index' class="tarea" :class="{done:tarea.done}" >{{ tarea.text }} <span @dblclick="eliminartarea(index)" @click="setDone(index)" class="boton">x</span></div>
      <!-- <div class="tarea" :class="{done:nuevatarea=='2'}" >Tarea 2 <span class="boton">x</span></div> -->
    </div>
    <div>
      <input v-model="nuevatarea" @keypress.enter="addtarea" type="text" placeholder="Escribe tu tarea">

      <p class="help" v-show="nuevatarea != ''">Sube tu tarea</p>
    </div>
  </div>
</template>

<style scoped>
.done{
  text-decoration: line-through;

}
  .card{
    background-color:#F2E9E4;
    max-width: 540px;
    border-radius: 8px;
    padding: 18px 16px;
    margin: 0 auto;
    font-family: 'Rubik', sans-serif;
  }
  h1{
    text-transform: uppercase;
    text-align: center;
    padding: 0;
    margin: 0;
    font-size: 24px;
  }
  .subtitulo{
    padding: 0;
    margin: 0;
    text-align: center;
    opacity: 0.8;
    margin-bottom: 5px;
  }
  .tarea{
    background-color: #C9ADA7;
    margin-bottom: 5px;
    padding: 3px 8px;
    max-width: 30%;
    border-radius: 4px;
  }
  .tarea:hover{
    background-color: #9A8C98;
  }
  .boton{
    float: right;
    display: inline-flex;
    align-items: center;
    background-color: #EDF2F4;
    border-radius: 4px;
    padding: 0 5px;
  }
  .boton:hover{
    background-color: #EF233C;
  }
  input{
    width: 100%;
    box-sizing: border-box;
    border: none;
    outline:none;
    padding: 3px 4px;
    border-radius: 4px;
  }
  .help{
    margin: 10px ;
    font-size: 13px;
    opacity: 0.7;
    text-align: center;
  }
  
</style>
