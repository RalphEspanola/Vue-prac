<script setup>
// Para sa additional Slides nga walay images
// const colors = ['indigo', 'warning', 'pink darken-2', 'red lighten-1', 'deep-purple accent-4']
// const additionalSlides = ['Fourth', 'Fifth']
</script>

<template>
  <v-carousel height="400" show-arrows="hover" cycle hide-delimiter-background>
    <!-- Using real images -->
    <v-carousel-item src="../../../public/images/Event1.jpg"> </v-carousel-item>

    <v-carousel-item src="../../../public/images/Event2.jpg"> </v-carousel-item>

    <v-carousel-item src="../../../public/images/Event3.jpg"> </v-carousel-item>
    <v-carousel-item src="../../../public/images/Event4.jpg"> </v-carousel-item>
    <v-carousel-item src="../../../public/images/Event5.jpg"> </v-carousel-item>

    <!-- Para ni sya sa mga slide nga di na need ug images -->
    <!-- <v-carousel-item v-for="(slide, i) in additionalSlides" :key="i + 3">
      <v-sheet :color="colors[i]" height="100%">
        <div class="d-flex fill-height justify-center align-center">
          <div class="text-h2">{{ slide }} Slide</div>
        </div>
      </v-sheet>
    </v-carousel-item> -->
  </v-carousel>
</template>
