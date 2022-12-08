<template>
  <v-card class="template">
    <!-- <div class="header">
        <h1 class="title">Home</h1>
        <p>This is the home page. It's a good idea to have a home page.</p>
      </div> -->
    <div class="center_div">
      <v-btn
        color="accent"
        large
        x-large
        v-for="tab in tabs"
        :key="tab"
        @click="selected = tab"
        :class="['tab-btn', { active: tab.includes(selected) }]"
      >
        {{ tab }}
      </v-btn>
    </div>
    <!-- display other components with selected -->
    <div v-if="selected === 'Flight'" class="tab">
      <FlightTabs />
    </div>
    <div v-if="selected === 'Hotel'" class="tab">
      <HotelTabs />
    </div>
    <div v-if="selected === 'Trips'" class="tab">
      <TripsTabs />
    </div>
  </v-card>
</template>

<script>
import FlightTabs from "../views/FlightTabs.vue";
import HotelTabs from "../views/HotelTabs.vue";
import TripsTabs from "../views/TripsTabs.vue";
export default {
  data: function () {
    return {
      tabs: ["Trips", "Flight", "Hotel"],
      selected: "Trips",
    };
  },
  components: {
    FlightTabs,
    HotelTabs,
    TripsTabs,
  },
};
</script>

<style>
.template {
  background: url("./../assets/images/background-place.jpg");
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
  height: 200px;
  background-color: blue;
  margin-top: -15px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.center_div {
  display: flex;
  align-items: center;
  justify-content: space-between;
  background: none;
  border: none;
  margin-top: 30px;
}
.header {
  color: #336699 !important;
  display: flex !important;
  flex-direction: column !important;
  align-items: center !important;
  justify-content: center !important;
}
.template {
  background: url("./../assets/images/background-manora.jpg");
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  /* height: 60vh; */
  display: flex;
  flex-direction: column;
  align-items: center;
  color: white;
}
.tab-btn {
  margin-bottom: 1rem;
  outline: none;
  padding: 20px 90px;
  margin-right: 50px;
  display: flex;
  text-align: center;
  color: #336699 !important;
}

.active {
  background-color: #336699;
  color: white !important;
}

.tab {
  padding: 10px;
  width: 1000px;
  height: 187px;
  background-color: #336699;
  margin-top: -15px;
  display: flex;
  justify-content: center;
  align-items: center;
  color: white;
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
