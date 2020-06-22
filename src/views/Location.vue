<template>
<v-carousel cycle height="92vh">
    <v-carousel-item
      v-for="(item,i) in items"
      :key="i"
      :src="item.src"
      
      reverse-transition="fade-transition"
      transition="fade-transition"
    ></v-carousel-item>
  </v-carousel>
</template>
<script>
  export default {
    data () {
      return {
        items: [
          {
            src: 'https://images2.alphacoders.com/593/593196.jpg',
          },
          {
            src: 'https://img5.goodfon.com/wallpaper/nbig/d/17/khram-iaponiia-osen-kioto.jpg',
          },
          {
            src: 'https://i.pinimg.com/originals/ec/f3/e0/ecf3e00cfbaa9af366fad7fd1d1ae629.jpg',
          },
          {
            src: 'https://www.fujisan-3776.jp/preservation/visitor-management/documents/04_1920-1080.jpg',
          },
        ],
      }
    },
  }
</script>