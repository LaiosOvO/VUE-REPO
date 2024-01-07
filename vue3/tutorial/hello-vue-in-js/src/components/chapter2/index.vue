<script setup>
import { ref } from 'vue';
import { nextTick  } from 'vue';
import { reactive  } from 'vue';

  const count = ref(0);
  console.log(count)
  console.log(count.value)

  count.value ++;
  console.log(count.value)

  function increment() {
    count.value++
  }
  
  const obj = ref( {
    nested: { count: 0 },
    arr: ['foo','bar']
  } )

  const returnOBJ = ()=>{
    return obj.value.nested.count
  }

  function cb1(){
    obj.value.nested.count++;
    obj.value.arr.push('aaaaaa')
  }

  async function increment2(){
    count.value++
    await nextTick()
  }

  const state = reactive( {count: 0} )


</script>

<template>
  <div>
    hi 响应式基础 in vue js

    
    <div class="Chapter_TWO">
      <h1>响应式基础</h1>
      <div @click="()=>{ count++ }" >{{count}}</div>
      <div @click="increment" >{{count}}</div>

      <h1>深层响应性</h1>
      <span>略</span>


      <h1>DOM更新时期</h1>
      <div>{{ count }}</div>
      <button @click="increment2" > 异步更新但是及时更新视图 </button>

      <h1>reactive()</h1>
      <button @click="state.count++" >
        {{ state.count }}
      </button>
    </div>




  </div>
</template>



<style scoped>

</style>
