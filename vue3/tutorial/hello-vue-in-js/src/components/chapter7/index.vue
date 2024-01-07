<script setup>
import { ref } from 'vue'
var count = ref(1);

function greet( event ){

  if( event ){
    alert( event.target.tagName )
  }
}

function say(message){
  alert( message );
}

function warn(message, event) {
  // 这里可以访问原生事件
  if (event) {
    event.preventDefault()
  }
  alert(message)
}

</script>

<template>


  <div>
    
    
    <div class="Chapter_7">

    <h1>内联事件处理器</h1>
    <button @click="()=>{
    count++;
    console.log( count )
    }" >add 1</button>
    <p> count is {{ count }} </p>


    <h1>方法事件处理器</h1>
    <button @click="greet" >Greet</button>

    <h1>在内联处理器中调用方法</h1>
    <button @click="say('hello')" >say hello</button>
    <button @click="say('bye')" >say bye</button>


    <h1>在内联事件处理器中访问事件参数</h1>
    <button @click="(event) => warn('Form cannot be submitted yet.', event)">
    Submit
    </button>

    <h1>事件修饰器</h1>



    </div>



  </div>
</template>


<style scoped>

</style>
