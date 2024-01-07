<script setup>
import { ref , computed, reactive } from 'vue';
  
  const author = reactive({
    name: 'John Doe',
    books: [
      'book1',
      'book2',
      'book3'
    ]
  })
  
  const publishedBooksMessage = computed( ()=>{
    // 一个快速的表达式用来表示转换关系的表达式
    //语法是 const var1 = computed( ()=>{ .... return ...; } )
    return author.books.length>=3? 'yes' : 'no';
  } )
  
  // 组件中
  function calculateBooksMessage() {
    return author.books.length > 0 ? 'Yes' : 'No'
  }
  
  
  const firstName = ref('John');
  const lastName = ref('John');
  const fullName = computed( {
  
    get(){
      return `${firstName.value} - ${lastName.value}  `
    },
    set( newValue ){
      [ firstName.value , lastName.value ] = newValue.split('')
    }
  
  } )
  
  


</script>

<template>
  <div>
    
    <div>
      <h1>计算属性</h1>
      <p>has published books:</p>      
      <span> {{ author.books.length>=3? 'yes' : 'no' }} </span>
      
      <span> {{ publishedBooksMessage }} </span>

      <h1>计算属性缓存 vs 方法</h1>
      <p> {{ calculateBooksMessage() }} </p>


      <h1>可写计算属性</h1>
      <p>通过 getter / setter 使用计算属性</p>
      <div>{{ fullName }}</div>


      <h1>最佳实践</h1>
      <p>避免副作用 = 不要使用异步操作</p>


    </div>



  </div>
</template>


<style scoped>

</style>
