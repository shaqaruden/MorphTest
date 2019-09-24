<template>
    <div>
      <h3 class="text-2xl font-bold px-4 py-2 pb-0">Share Something!</h3>
      <section class="flex overflow-x-auto scrolling-touch min-w-full px-2 py-4 section">
      <div class="card h-48 px-2">
        <div class="bg-red-500 h-full rounded-lg item1 z-50">
          <button v-if="morphed === '.item1'" class="font-bold text-white absolute pin-t pin-l m-2 mx-3 cursor-pointer" @click="morphAnimation.reverse">X</button>
          <button v-if="morphed !== '.item1'" class="w-full h-full text-white font-bold" @click="morph('.item1')">Click Me!</button>
        </div>
      </div>
      <div class="card h-48 px-2">
        <div class="bg-blue-500 h-full rounded-lg item2 z-10">
          <button class="w-full h-full text-white font-bold" @click="morph('.item2')">Click Me!</button>
        </div>
      </div>
      <div class="card h-48 px-2">
        <div class="bg-green-500 h-full rounded-lg item3 z-10">
          <button class="w-full h-full text-white font-bold" @click="morph('.item3')">Click Me!</button>
        </div>
      </div>
      <div class="card h-48 px-2">
        <div class="bg-orange-500 h-full rounded-lg item4 z-10">
          <button class="w-full h-full text-white font-bold" @click="morph('.item4')">Click Me!</button>
        </div>
      </div>
    </section>
    </div>
</template>

<script>
import anime from 'animejs/lib/anime.es.js';

export default {
  name: 'app',
  data() {
    return {
      morphed: '',
      morphAnimation: {}
    }
  },
  methods: {
    morph(item) {
      this.morphed = item
      document.querySelector(item).style.position = 'absolute'
      document.querySelector(item).style.height = '192px'
      document.querySelector(item).style.width = '208px'
      this.morphAnimation = anime({
        targets: item,
        left: 0,
        top: 0,
        borderRadius: ['.5rem', '0rem'],
        margin: '0',
        width: "100vw",
        height: "35vh",
        easing: "easeInOutQuad",
        duration: '400',
        begin: (anim => {
          this.active = true
        })
      });
    }
  }
}
</script>

<style scoped>
.section {
  scroll-snap-type: x mandatory;
}
.card {
  min-width: 224px;
  scroll-snap-align: center;
  scroll-snap-stop: always;
}
</style>