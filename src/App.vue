<template>
  <div id="app" class="big-container">
    <v-header></v-header>
    <!-- <v-emoji></v-emoji> -->
    <v-piano></v-piano>
  </div>
</template>

<script>
import VHeader from '@/components/VHeader'
// import VEmoji from '@/components/VEmoji'
import VPiano from  '@/components/VPiano'
export default {
  name: "App",
  components: {
    VHeader,
    // VEmoji,
    VPiano,
  },
};

</script>

<style lang="postcss" scoped>
.big-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: 0;
  padding: 0;
  height: 98vh;
}

#app {
    background: linear-gradient(135deg, #ff9d6c, #bb4e75);
       background-size: 400% 400%;
        -webkit-animation: AnimationName 8s ease infinite;
        -moz-animation: AnimationName 8s ease infinite;
        animation: AnimationName 8s ease infinite;
}

@-webkit-keyframes AnimationName {
    0%{background-position:0% 50%}
    50%{background-position:100% 51%}
    100%{background-position:0% 50%}
}
@-moz-keyframes AnimationName {
    0%{background-position:0% 50%}
    50%{background-position:100% 51%}
    100%{background-position:0% 50%}
}
@keyframes AnimationName { 
    0%{background-position:0% 50%}
    50%{background-position:100% 51%}
    100%{background-position:0% 50%}
}

@media (max-width: 700px) {
  .big-container {
    justify-content: space-around;
  }
  .container-piano,
  .container-emoji,
  .container-title {
    margin: 0;
  }
}
</style>