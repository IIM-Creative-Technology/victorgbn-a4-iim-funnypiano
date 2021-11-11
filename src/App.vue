<template>
  <div id="app" class="big-container">
    <v-header></v-header>
    <v-emoji></v-emoji>
    <v-piano></v-piano>
  </div>
</template>

<script>
import VHeader from '@/components/VHeader'
import VEmoji from '@/components/VEmoji'
import VPiano from  '@/components/VPiano'
export default {
  name: "App",
  components: {
    VHeader,
    VEmoji,
    VPiano,
  },
};

</script>

<style lang="postcss" scoped>
.big-container {
  display: flex;
  flex-direction: column;
  align-items: center;
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