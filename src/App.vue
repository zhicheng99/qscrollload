<template>
  <div id="app">

    滚动
    <div class="lay">

      <qscrollload>
        
        <div>
          fsfsfdsds<br>
          fsfsfdsds<br>
          fsfsfdsds<br>
          fsfsfdsds<br>
          fsfsfdsds<br>
          fsfsfdsds<br>fsfsfdsds<br>
          fsfsfdsds<br>
          fsfsfdsds<br>
          fsfsfdsds<br>
          fsfsfdsds<br>
          fsfsfdsds<br>
          fsfsfdsds<br>
          fsfsfdsds<br>fsfsfdsds<br>
          fsfsfdsds<br>
          fsfsfdsds<br>
          fsfsfdsds<br>
          fsfsfdsds<br>
          fsfsfdsds<br>
          fsfsfdsds<br>
          fsfsfdsds<br>fsfsfdsds<br>
          fsfsfdsds<br>
          fsfsfdsds<br>
          fsfsfdsds<br>
          fsfsfdsds<br>
          fsfsfdsds<br>
          fsfsfdsds<br>
          fsfsfdsds<br>fsfsfdsds<br>
          fsfsfdsds<br>
          
        </div>

      </qscrollload>    
    </div>

    下拉刷新
    <div class="lay">
      <qscrollload
       v-bind:refresh-fun="refreshFun"
       >
        
        <div>
          fsfsfdsds<br>
          fsfsfdsds<br>
          fsfsfdsds<br>
          fsfsfdsds<br>
          fsfsfdsds<br>
          fsfsfdsds<br>fsfsfdsds<br>
          fsfsfdsds<br>
          fsfsfdsds<br>
          fsfsfdsds<br>
          fsfsfdsds<br>
          fsfsfdsds<br>
          fsfsfdsds<br>
          fsfsfdsds<br>fsfsfdsds<br>
          fsfsfdsds<br>
          fsfsfdsds<br>
          fsfsfdsds<br>
          fsfsfdsds<br>
          fsfsfdsds<br>
          fsfsfdsds<br>
          fsfsfdsds<br>fsfsfdsds<br>
          fsfsfdsds<br>
          fsfsfdsds<br>
          fsfsfdsds<br>
          fsfsfdsds<br>
          fsfsfdsds<br>
          fsfsfdsds<br>
          fsfsfdsds<br>fsfsfdsds<br>
          fsfsfdsds<br>
          
        </div>

      </qscrollload>
    </div>

  <test></test>
  </div>
</template>

<script> 

import qscrollload from "./qscrollload.vue";
import test from "./test.vue";


export default {
  name: "App",
  components: {
    qscrollload,
    test
  },
  data() {
    return { 
       
    }
  },
  methods: { 
    refreshFun:function(){

      return new Promise((resolve,reject)=>{


          setTimeout(()=>{
            resolve('ok');
          },2000)

      })

    },
    save:function(json){

      console.log(json);

    }
  },
};
</script>

<style scoped>
  .lay{
    width: 200px;
    height: 400px;
    position: relative;
    background-color: #eee;
  }

</style>
