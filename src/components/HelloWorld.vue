<template>
  <div class="hello">
    <h1>{{tit}}</h1>
    <h2>{{user}}</h2>
    <button @click="onClick">改变值</button>
    <p>{{result}}</p>
  </div>
</template>

<script>
import {reactive,ref,onMounted,computed,watchEffect } from 'vue'
export default {
  name: 'HelloWorld',
  setup(){
    const data = reactive({
      name:'Hello world',
      num:0
    })
    const tit = data.name;
    const user = ref("maomin");
    const onClick = ()=>{
       user.value = "xqm";
    } 
    onMounted(()=>{
      console.log("onMounted!")
    })
    const count = ref(0);
    const result = computed(()=>{
      // return data.num+1
      return count.value + 1
    })
    const watchResult = watchEffect(()=>{
      console.log('watch')
      // document.body.innerHTML = `count is ${user.value}`
    })
    return {tit,user,onClick,result,computed,watchResult}
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
