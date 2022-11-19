<template>
  <v-card class="home">
    <v-card class="template">
      <h1 class="title">Home</h1>
      <p>This is the home page. It's a good idea to have a home page.</p>
      <div class="center_div">
        <v-btn
          color="accent"
          large
          x-large
          v-for="tab in tabs"
          :key="tab"
          @click="selected = tab"
          :class="['tab-btn', { active: selected === tab }]"
        >
          {{ tab }}
        </v-btn>
      </div>
      <component :is="selected" class="tab"></component>
    </v-card>
  </v-card>
</template>

<script>
export default {
  data: function () {
    return {
      tabs: ["Trips", "Flight", "Hotel"],
      selected: "Trips",
    };
  },
  components: {},
};
</script>

<style>
.template {
  background: url("./../assets/background-place.jpg");
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  height: 60vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  color: white;
  justify-content: center;
}
.tab-btn {
  margin-bottom: 1rem;
  outline: none;
  padding: 20px 90px;
  margin-right: 50px;
  display: flex;
  text-align: center;
  color: blue !important;
}

.active {
  background-color: red;
}

.tab {
  padding: 10px;
  width: 1000px;
  height: 150px;
  background-color: blue;
  margin-top: -15px;
}
.center_div {
  display: flex;
  align-items: center;
  justify-content: space-between;
  background: none;
  border: none;
  margin-top: 30px;
}
</style>
