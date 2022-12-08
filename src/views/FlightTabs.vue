<template>
  <div class="flights col">
    <form class="flights">
      <div class="center row">
        <div class="col box">
          <!-- label for Select FLights-->
          <label for="selectFlights">Select Flights</label>
          <div class="row">
            <!-- search autocomplete for flying from -->
            <v-text-field
              v-model="flyingFrom"
              label="Flying From"
              placeholder="Flying From"
              type="search"
              class="col"
              :items="airports"
              item-text="name"
              item-value="code"
              autocomplete
              clearable
              outlined
              dense
            ></v-text-field>
            <!-- search autocomplete for flying to -->
            <v-text-field
              v-model="flyingTo"
              label="Flying To"
              placeholder="Flying To"
              type="search"
              class="col"
              :items="airports"
              item-text="name"
              item-value="code"
              autocomplete
              clearable
              outlined
              dense
            ></v-text-field>
          </div>
        </div>
        <div class="col box">
          <!-- label for Select Travel Dates -->
          <label for="selectTravelDates">Select Travel Dates</label>
          <div class="row">
            <v-text-field
              v-model="departDate"
              label="Depart Date"
              type="date"
              class="wid"
            ></v-text-field>
            <v-text-field
              v-model="returnDate"
              label="Return Date"
              type="date"
              class="wid"
              @change="departureDate"
              v-if="checkDepDate"
            ></v-text-field>
          </div>
        </div>
        <div class="col boxs">
          <!-- label for passengers -->
          <label for="passengers">Passengers</label>
          <div class="passengers">
            <v-text-field
              v-model="passengers"
              label="Passengers"
              dense
              rounded
              class="wid"
            ></v-text-field>
          </div>
        </div>
        <div class="search">
          <v-btn
            class="ma-2"
            :loading="loading"
            :disabled="loading"
            color="secondary"
            @click="loader = 'loading'"
          >
            Search
          </v-btn>
        </div>
      </div>
      <div class="row box pad">
        <!-- dropdown for one way or roundtrip -->
        <v-select
          v-model="oneWay"
          :items="oneWayOptions"
          label="One Way or Round Trip"
          dense
          rounded
          class="wid"
          @click="hello"
        ></v-select>
        <!-- dropdown for class -->
        <v-select
          v-model="classy"
          :items="classOptions"
          label="Class"
          class="wid"
        ></v-select>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      flyingFrom: null,
      flyingTo: null,
      departureDate: " ",
      returnDate: null,
      departureDateMenu: false,
      returnDateMenu: false,
      loader: null,
      loading: false,
      oneWay: null,
      oneWayOptions: ["One Way", "Round Trip"],
      classy: null,
      classOptions: ["Economy", "Business", "First Class"],
      airports: [],
      checkDepDate: true,
      departDate: null,
    };
  },
  methods: {
    hello() {
      // insert values to airports their name of place for airport
      this.airports.insert({ name: "name of place", code: "code of place" });
    },
    getAirports() {
      // use axios to import from https://airport-info.p.rapidapi.com/airport
      const axios = require("axios").default;
      const options = {
        method: "GET",
        url: "airport-info.p.rapidapi.com/airport",
        headers: {
          "X-RapidAPI-Key":
            "ab0af44cf9msh2a4230be3397f51p16692cjsn63dd3957cdc4",
          "X-RapidAPI-Host": "airport-info.p.rapidapi.com",
        },
      };

      axios
        .request(options)
        .then(function (response) {
          console.log(response.data);
        })
        .catch(function (error) {
          console.error(error);
        });
    },
  },
};
</script>

<style>
.row {
  display: flex;
  flex-direction: row;
}
.col {
  display: flex;
  flex-direction: column;
}
.wid {
  width: 150px;
}
.box {
  width: 300px;
  margin-right: 30px;
}
.boxs {
  width: 150px;
  margin-right: 30px;
}
.center {
  display: flex;
  justify-content: center;
  align-items: center;
}
.pad {
  margin-left: 15px;
}
</style>
