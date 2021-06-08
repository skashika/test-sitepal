<template>
  <v-app>
    <v-main>
      <router-view/>
    </v-main>
  </v-app>
</template>

<script>

export default {
  name: 'App',

  data: () => ({
    //
  }),
  methods:{
    loadEmbedFile() {
      const that = this
      var sc = document.createElement('script');
      sc.type = "text/javascript";
      sc.src = "//vhss-d.oddcast.com/vhost_embed_functions_v4.php?acc=7295865&js=0";
      sc.onload = function () {
        that.callEmebedFunction();
      }
      document.head.appendChild(sc);
    },
    callEmebedFunction() {
      setTimeout(() => {
        if (typeof AC_VHost_Embed == 'function') {
          //clearInterval(interval);
          var script = document.createElement('script');
          script.type = "text/javascript";
          script.innerHTML =
              "AC_VHost_Embed(7295865,600,800,'',1,0,2712925,0,1,0,'kViNiZyNSfcW9uKZf15raB7GhZY4qvBa',0, '400|300|15|15|L|T|false|0|0|0|0|vhss.oddcast.com/ccs2/vhss/user/0d4/6880888/thumbs/show_2639704.jpg|Double%20click%20to%20play%20me|0|C|0|0|0|992')";
          console.log(script)
          document.getElementById('divVHSS').appendChild(script);
        }
      }, 0)
    }
  },
  mounted() {
    this.loadEmbedFile()
  }
};
</script>
<style>
html, body {
  margin: 0;
  height: 100%;
  overflow: hidden
}

body::-webkit-scrollbar {
  display: none;
}
</style>
