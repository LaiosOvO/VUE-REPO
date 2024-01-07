<script setup>
import { ref , reactive } from 'vue';

const parentMessage = ref('Parent')
const items = ref([{ message: 'Foo' }, { message: 'Bar' }])

const myObject = reactive({
  title: 'How to do lists in Vue',
  author: 'Jane Doe',
  publishedAt: '2016-04-10'
})


</script>

<template>


  <div>
    


    
    <div>
      <h1>v-for</h1>
      <li v-for="item in items">
        {{ item.message }}
      </li>

      <li v-for="(item, index) in items">
        {{ parentMessage }} - {{ index }} - {{ item.message }}
      </li>
      
      <h1>通过解构赋值</h1>
      <li v-for="{ message } in items">
        {{ message }}
      </li>

      <!-- 有 index 索引时 -->
      <li v-for="({ message }, index) in items">
        {{ message }} {{ index }}
      </li>

      <h1>v-for 与对象</h1>
      <ul>
        <li v-for="value in myObject">
          {{ value }}
        </li>
      </ul>
      
      <li v-for="(value, key) in myObject">
        {{ key }}: {{ value }}
      </li>
      
      <li v-for="(value, key, index) in myObject">
        {{ index }}. {{ key }}: {{ value }}
      </li>

      <h1>在v-for 里使用范围值</h1>
      <span v-for="n in 10">{{ n }}</span>

      <template v-for="todo in todos">
        <li v-if="!todo.isComplete">
          {{ todo.name }}
        </li>
      </template>

      <h1>数组变化侦测</h1>


      
    </div>



  </div>
</template>


<style scoped>

</style>
