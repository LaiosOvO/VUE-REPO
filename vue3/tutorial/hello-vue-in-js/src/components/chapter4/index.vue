<script setup>
import { ref , computed } from 'vue';


var isActive = ref(true);
var error = ref(null);
var hasError = false;

const classObject = computed(() => ({
  active: isActive.value && !error.value,
  'text-danger': error.value && error.value.type === 'fatal'
}))



const activeClass = ref('active')
const errorClass = ref('text-danger')


const activeColor = ref('red')
const fontSize = ref(30)



</script>

<template>


  <div>
    <h1>hi vue in js</h1>


    <div class="chapter4" >
      <h1>绑定 HTML class</h1>
      <div 
      class="static"
      :class="{ active: isActive , 'text-danger': hasError }" >
        normal bind the class attr
      </div>
      <div 
      class="static"
      :class="classObject" >
        computed bind the class attr
      </div>

      <h1>绑定数组</h1>
      <div :class="[ activeClass , errorClass ]" >绑定数组</div>

      <h1>绑定内联样式</h1>
      <h2>绑定对象</h2>
      <div :style="{ 'font-size':fontSize + 'px' }" >......</div>
      
      <h2>绑定数组</h2>
      <div :style="[ baseStyle , overrideStyles ]" ></div>


      


    </div>



  </div>
</template>


<style scoped>

</style>
