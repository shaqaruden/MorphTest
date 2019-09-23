<template>
  <div class="flex-1 flex flex-col items-center">
    <div class="bg-green-500 rounded-lg m-4 morph relative" @click="morph">
      <button v-show="active" class="mt-1 ml-3 text-white absolute close" style="opacity: 0;" @click="unMorph">
        <i class="fa fa-times fa-2x"></i>
      </button>
      <button class="p-4 activator" v-if="!active">
        <img class="h-16" src="../assets/dropbox.png" alt />
      </button>
    </div>
    <div class="w-screen h-full bg-white mt-64 absolute content" style="opacity: 0; border-radius: 2rem"></div>
  </div>
</template>

<script>
import anime from 'animejs/lib/anime.es.js';

export default {
  name: "HelloWorld",
  data() {
    return {
      active: false,
      morphAnime: null,
      activatorAnime: null,
      contentAnime: null,
      closeAnime: null
    }
  },
  methods: {
    morph() {
      this.morphAnime = anime({
        targets: ".morph",
        borderRadius: ['.5rem', '0rem'],
        margin: '0',
        width: "100vw",
        height: "30vh",
        easing: "easeInOutQuad",
        duration: '500',
        begin: (anim => {
          this.active = true
        })
      });
      this.activatorAnime = anime({
        targets: ".activator",
        opacity: 0,
        easing: 'easeInOutQuad',
        duration: '500'
      });
      this.contentAnime = anime({
        targets: ".content",
        opacity: "1",
        top: "-4rem",
        easing: 'easeInOutQuad',
        delay: '50',
        duration: '500'
      });
      this.closeAnime = anime({
        targets: ".close",
        opacity: "1",
        easing: 'easeInOutQuad',
        delay: '50',
        duration: '500'
      });
    },
    unMorph() {
      this.morphAnime.reverse
      this.activatorAnime.reverse
      this.contentAnime.reverse
      this.closeAnime.reverse
    }
  }
};
</script>

<style scoped>
.dropbox {
  fill: orange;
}
</style>