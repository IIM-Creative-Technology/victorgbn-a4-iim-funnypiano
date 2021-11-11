<template>
  <div class="container-emoji">
    <img alt="GIF trop drôle" id="imgGif" :src="src" v-if="src" />
  </div>
</template>

<script>
import { GiphyFetch } from "@giphy/js-fetch-api";
export default {
  GiphyFetch,
  mounted() {},

  data() {
    return {
      src: null,
    };
  },

  methods: {
    async pickEmoji() {
      const gf = new GiphyFetch("hoc7Xw81iwUP2iewXhekupQznVmYDlHK");
      const { data: gifs } = await gf.emoji();
      const nbRandom = Math.floor(Math.random() * 25);
      const gif = gifs[nbRandom].images.downsized.url;
      this.src = gif;
    },
  },
};
</script>

<style lang="postcss" scoped>
.container-emoji {
  width: 200px;
  height: 200px;
  margin-top: 29px;
}
.container-emoji img {
  border-radius: 20px;
  width: 100%;
  height: 100%;
  filter: drop-shadow(0 0 0.75rem crimson);
}
</style>