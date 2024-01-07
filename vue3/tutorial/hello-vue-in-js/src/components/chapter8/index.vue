<script setup>
import {ref} from 'vue'

const val = "123321";
const val2 = "123123123";
const myMessage = "value of the string ";
const checked = true;
const checkedNames = ref([])
const picked = ref('One')
const selected = ref('')
const selected2 = ref([])
const toggle = ref(false)



</script>

<template>


  <div>
    <h1>hi vue in js</h1>
    <h1>表单输入绑定</h1>
    <input type="text"
      :value="val"
      @input=" e => val=e.target.value "
    >
    <input type="text"
      v-model="val2"
    >


    <h2>基本用法</h2>
    <p>message is {{ myMessage }}</p>
    <input type="text" placeholder="edit me" v-model="myMessage" >

    <h2>复选框</h2>    
    <input type="checkbox" id="checkbox" v-model="checked">
    <label for="checkbox" > {{ checked }} </label>
    
    <div>Checked names: {{ checkedNames }}</div>

    <input type="checkbox" id="jack" value="Jack" v-model="checkedNames">
    <label for="jack">Jack</label>

    <input type="checkbox" id="john" value="John" v-model="checkedNames">
    <label for="john">John</label>

    <input type="checkbox" id="mike" value="Mike" v-model="checkedNames">
    <label for="mike">Mike</label>
    
    <h2>单选按钮</h2>
    <div>Picked: {{ picked }}</div>

    <input type="radio" id="one" value="One" v-model="picked" />
    <label for="one">One</label>

    <input type="radio" id="two" value="Two" v-model="picked" />
    <label for="two">Two</label>

    <h2>选择器</h2>
    <div>Selected: {{ selected }}</div>

    <select v-model="selected">
      <option disabled value="">Please select one</option>
      <option>A</option>
      <option>B</option>
      <option>C</option>
    </select>

    <div>Selected: {{ selected2 }}</div>
    <select v-model="selected2" multiple>
      <option>A</option>
      <option>B</option>
      <option>C</option>
    </select>

    <h2>值绑定</h2>
    <!-- `picked` 在被选择时是字符串 "a" -->
    <input type="radio" v-model="picked" value="a" />
    <label for=""></label>

    <!-- `toggle` 只会为 true 或 false -->
    <input type="checkbox" v-model="toggle" />

    <!-- `selected` 在第一项被选中时为字符串 "abc" -->
    <select v-model="selected">
      <option value="abc">ABC</option>
    </select>

  </div>
</template>


<style scoped>

</style>
