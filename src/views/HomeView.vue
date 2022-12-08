<template>
  <v-card class="stores">
    <v-carousel show-arrows="hover" cycle class="caro">
      <!-- loop the v-carousel-item -->
      <v-carousel-item
        v-for="item in items"
        :key="item"
        :src="item.src"
        :lazy-src="item.lazySrc"
        :alt="item.alt"
        :transition="item.transition"
        cover
      >
        <div class="end">
          <h1 class="title">Home</h1>
          <p>This is the home page. It's a good idea to have a home page.</p>
          <div class="pad-top">
            <OpenTabs />
          </div>
        </div>
      </v-carousel-item>
    </v-carousel>
  </v-card>
</template>

<script>
import OpenTabs from "../views/OpenTabs.vue";
import { ref } from "vue";
export default {
  data: () => {
    return {
      isOpen: ref(false),
      items: [
        {
          src: "https://cdn.vuetifyjs.com/images/carousel/squirrel.jpg",
          lazySrc: "https://cdn.vuetifyjs.com/images/carousel/squirrel.jpg",
          alt: "Squirrel",
          transition: "fade-transition",
        },
        {
          src: "https://cdn.vuetifyjs.com/images/carousel/sky.jpg",
          lazySrc: "https://cdn.vuetifyjs.com/images/carousel/sky.jpg",
          alt: "Sky",
          transition: "fade-transition",
        },
        {
          src: "https://cdn.vuetifyjs.com/images/carousel/bird.jpg",
          lazySrc: "https://cdn.vuetifyjs.com/images/carousel/bird.jpg",
          alt: "Bird",
          transition: "fade-transition",
        },
        {
          src: "https://cdn.vuetifyjs.com/images/carousel/planet.jpg",
          lazySrc: "https://cdn.vuetifyjs.com/images/carousel/planet.jpg",
          alt: "Planet",
          transition: "fade-transition",
        },
      ],
    };
  },
  components: {
    OpenTabs,
  },
};
</script>
<style>
/* design the show-arrows */
.v-carousel__controls {
  background-color: rgba(0, 0, 0, 0.5);
}
.pad-top {
  padding-top: 100px;
}
.root {
  position: relative;
}
.end {
  right: 400px;
  top: 300px;
  margin: 20px;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding-top: 100px;
}
.highlight {
  height: inherit;
  width: 900px;
  display: flex;
  flex-direction: column;
  align-items: center;
  color: white;
  justify-content: center;
  background-color: rgb(140, 0, 255);
}
.highlight_tabs {
  width: 400px;
  height: inherit;
  display: flex;
  flex-direction: column;
  align-items: center;
  color: white;
  justify-content: center;
  background-color: aqua;
}
.inside_stores {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  color: white;
  background-color: white;
  height: 400px;
  width: 1300px;
}
.stores {
  display: flex;
  flex-direction: column;
  align-items: center;
  color: white;
  justify-content: center;
  background-color: black;
}
.caro {
  background-color: black;
}
</style>
