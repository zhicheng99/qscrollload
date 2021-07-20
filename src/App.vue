<template>
  <div id="app">

    
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
  }

</style>
