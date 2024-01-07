<script setup>
import { ref, watch,reactive } from 'vue'

const question = ref('')
const answer = ref('Questions usually contain a question mark. ;-)')
const loading = ref(false)

watch(question, async (newQuestion, oldQuestion) => {
  if (newQuestion.includes('?')) {
    loading.value = true
    answer.value = 'Thinking...'
    try {
      const res = await fetch('https://yesno.wtf/api')
      answer.value = (await res.json()).answer
    } catch (error) {
      answer.value = 'Error! Could not reach the API. ' + error
    } finally {
      loading.value = false
    }
  }
})


const x = ref(0)
const y = ref(0)
watch( x, (ori) => {
  console.log( ` x is ${ ori } ` )
} )

watch(
  ()=> x.value+y.value,
  (sum)=>{
    console.log(` sum of x + y is ${sum} `)
  }
)

// 多个数据源
watch( [ x,()=>y.value ] ,( [oriX,oriY] )=>{
  console.log(` cur value is { ${ oriX } - ${oriY} } `)
} )


const obj = reactive( { count: 0 } )
watch( obj , ( newv,oldv )=>{


  console.log("async function is invoked at time"+Date.now())

} ,
{ deep: true }
)


const source = reactive( {
  immediate: true
} )

watch(
  source,
  (newV,oldV) => {
    console.log("is invoked immediatly")
  },
  { immediate:true }
)

const todoId = ref(1)
const data = ref(null)

/**

watch(
  todoId,
  async () => {
    const response = await fetch(
      `https://jsonplaceholder.typicode.com/todos/${todoId.value}`
    )
    data.value = await response.json()

    console.log(data.value)
  },
  { immediate: true }
)

 */

watchEffect(async () => {
  const response = await fetch(
    `https://jsonplaceholder.typicode.com/todos/${todoId.value}`
  )
  data.value = await response.json()
})
</script>

<template>

  <h1>hi vue in js</h1>

  <div>
    <h1>侦听器</h1>

    <h2>基本实例</h2>
    <p>
      Ask a yes/no question:
      <input v-model="question" :disabled="loading" />
    </p>
    <p>{{ answer }}</p>



    <h2>侦听数据源类型</h2>
    <button @click="x++">change x</button>
    <button @click="x+=10">change x base 10</button>


    <h2>深层侦听器</h2>
    <button @click="()=>{ obj.count++  }" >change obj value</button>


    <h2>及时回调的侦听器</h2>
    <p>{{ source.immediate }}</p>
    <button @click="source.immediate = !source.immediate;" >change source obj value</button>

    <h2>watchEffect()</h2>
    <p>{{ data.title }}</p>
    <button @click="todoId++" >change todoId</button>
    <p>语法糖</p>
    <p>{{ data.title }}</p>

    <h2>回调的触发时机</h2>
    


  </div>

</template>


<style scoped>

</style>
