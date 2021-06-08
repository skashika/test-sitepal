<template>
  <v-container fluid id="avatar-wrapper"
               class="pa-0 ma-0"
               :style="{ height: height + 'px', width : width + 'px'}">
    <div id="divVHSS"></div>
  </v-container>
</template>

<script>
export default {
  name: "avatar",
  props: {
    initialWidth: {
      type: Number,
      required: true
    },
    textBubble: {
      type: String,
      default: "bottom"
    }
  },
  data() {
    return {
      width: this.initialWidth,
      bubbleText: '',
      curLanguage: 'en',
    }
  },
  computed: {
    height: {
      get() {
        return this.width * 1.125
      },
      set(newVal) {
        this.width = newVal * 8 / 9
      }
    },
    spVoice: function () {
      switch (this.curLanguage) {
        case 'es':
          return 4;
        default: // en
          return 3;
      }
    },
    spLang: function () {
      switch (this.curLanguage) {
        case 'es':
          return 2;
        default: // en
          return 1;
      }
    },
    spEngine: function () {
      switch (this.curLanguage) {
        case 'es':
          return 4;
        default: // en
          return 3;
      }
    }
  },
  watch: {
    width: function () {
      console.log('What is the width', this.width)
      window.dynamicResize(this.width * 1.5, this.height);
    }
  },
  methods: {
    speak(speakText) {
      this.stopSpeak()
      console.log('Speaking Text', speakText)
      window.sayText('<prosody rate="+15%">' + speakText + '</prosody>', 3, 1, 3);
    },
    showResponse: function (response) {
      this.bubbleText = response;
    },
    stopSpeak() {
      window.stopSpeech();
    },
    forceResize: function () {
      window.dynamicResize(this.width * 1.5, this.height);
    }
  },
  mounted(){
    const that = this
    window.vh_sceneLoaded = function() {
      that.forceResize()
    }
    window.vh_talkStarted = function(){
      console.log('Called everytime speech started to stop recognition')
    }
  }
}
</script>

<style scoped>

</style>
