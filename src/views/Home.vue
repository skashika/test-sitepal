<template>
  <v-row no-gutters class="fill-height">
    <v-col cols="6">
      <avatar :initial-width="avatarWidth"></avatar>
    </v-col>
    <v-col cols="6" align="center" justify="center" id="row">
      <v-btn @click="call1()" class="ma-5" color="primary"> Info about Error </v-btn>
      <br>
      <v-btn @click="call2()" class="ma-5" color="primary"> Sentence 1 </v-btn>
      <br>
      <v-btn @click="call2()" class="ma-5" color="primary"> Sentence 2 </v-btn>
      <br>
      <v-btn @click="call2()" class="ma-5" color="primary"> Sentence 3 </v-btn>
    </v-col>
  </v-row>

</template>

<script>
import avatar from "@/components/avatar";

  export default {
    name: 'Home',
    computed:{
      avatarWidth(){
        return window.innerWidth / 2
      }
    },
    components: {
      avatar
    },
    methods:{
      call1(){
        avatar.methods.speak('This is just for testing purpose. To see the error please click on the buttons below without waiting for speech to end')
      },
      call2(){
        avatar.methods.speak('I am speaking please check console for errors')
      }
    }
  }
</script>
<style>

/deep/ #divVHSS-inner{
  z-index: -1 !important;
}

#row{
  z-index: 99999999 !important;
}
</style>
