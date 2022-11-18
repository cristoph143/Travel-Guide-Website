<template>
  <v-app>
    <TheNavigation />
    <v-main>
      <router-view />
    </v-main>
  </v-app>
</template>

<script>
// Components
import TheNavigation from "@/components/TheNavigation.vue";

export default {
  name: "App",

  components: {
    TheNavigation,
  },
};
</script>
