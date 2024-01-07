<template>
  <div>
    <h1>hi 模板语法</h1>
      <div>
        <h1>模板语法</h1>
        <span> message in the 模板语法 = {{msg}} </span>
        
        <h1>原始html</h1>
        <p>Using text interpolation: {{ rawHtml }}</p>
        <p>Using v-html directive: <span v-html="rawHtml"></span></p>
        
        <h1>attribute 绑定</h1>
        <div v-bind:id="randomId">{{randomId}}</div>
        <div :id="randomId">{{randomId}}</div>

        <h1>动态绑定多个值</h1>
        <div v-bind="objectOfAttr" >1111</div>

        <h1>使用js表达式</h1>
        <div> {{  Math.random() > 0.5? "good":"not good"  }} </div>

        <h1>调用函数</h1>
        <div> {{cb1()}} </div>

        <h1>指令</h1>
        <p>v-if</p>
        <div v-if="seen">can you see?</div>
        
        <h1>参数</h1>
        <a :href="u">link</a>
        <div v-on:click="cb1" >callback1</div>
        <div @click="cb2" > callback2 </div>

        <h1>动态参数</h1>
        <p>在html标签中的 [attr1]  这里的 attr1 会动态变化 可以动态设置上</p>
        <a v-bind:[attributeName]="url" @click="changeAttrKey"> ... </a>
        <a :[attributeName]="url"> ... </a>
      </div>
  </div>

</template>

<script setup>

var msg = "hello";
  var randomId = Math.random();

  var objectOfAttr = {
    theme: "dark",
    fontSize: 12
  }

  function cb1(){
    console.log("callback1()")
    return "first callback in the script section";
  }

  function cb2(){
    console.log("callback2()")
    return "second callback in the script section";
  }
  var seen = true;
  var u = "www.bing.com";

  var attributeName = "id";
  var changeAttrKey = ()=>{
    if(Math.random() >0.5){
      attributeName = "id";
    }else {
      attributeName = "class";
    }

  }


</script>

<style scoped>

</style>