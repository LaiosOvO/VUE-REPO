<script setup>
import { ref, watch,reactive,onMounted  } from 'vue'
import ButtonCounter from './ButtonCounter.vue'
import BlogPost  from './BlogPost.vue'
import AlertBox  from './AlertBox.vue'
import Home  from './Home.vue'
import Posts  from './Posts.vue'
import Archive  from './Archive.vue'


const posts = ref([
  { id: 1, title: 'My journey with Vue' },
  { id: 2, title: 'Blogging with Vue' },
  { id: 3, title: 'Why Vue is so fun' }
])


const postFontSize = ref(1)
const currentTab = ref('Home')

const tabs = {
  Home,
  Posts,
  Archive
}
console.log(tabs)

const aaaa = {
  props: ['postTitle'],
  emits: ['updatePost'],
  template: `
    <h3>{{ postTitle }}</h3>
  `
}

</script>

<template>

  <div>
    <h1>组件基础</h1>

    <h2>使用组件</h2>
    <ButtonCounter />
    <button-counter></button-counter>

    <h2>传递 props</h2>
    <BlogPost title="My journey with Vue" />
    <BlogPost title="Blogging with Vue" />
    <BlogPost title="Why Vue is so fun" />

    <h2>传递参数是复杂对象通过循环</h2>
    <BlogPost
      v-for="post in posts"
      :key="post.id"
      :title="post.title"
    />

    <h2>监听事件</h2>
    <p>简单来说就是子组件触发事件（定义事件名）+ 父组件处理事件</p>
    <div :style="{ fontSize: postFontSize + 'em' }">
    <BlogPost
      v-for="post in posts"
      :key="post.id"
      :title="post.title"
      @enlarge-text="postFontSize += 0.1"
    ></BlogPost>


    <h2>通过插槽来分配内容</h2>
    <p>简单来说就是 react里面 children</p>
    <AlertBox>
      Something bad happened.
    </AlertBox>

    <h2>动态组件</h2>
    <div class="demo">
      <button
        v-for="(_, tab) in tabs"
        :key="tab"
        :class="['tab-button', { active: currentTab === tab }]"
        @click="currentTab = tab"
      >
        {{ tab }}
      </button>
      <component :is="tabs[currentTab]" class="tab"></component>
    </div>





</div>

  </div>


</template>


<style scoped>

</style>
