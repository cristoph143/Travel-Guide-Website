<template>
  <div class="flights col">
    <form class="flights">
      <div class="center row">
        <div class="col box">
          <!-- label for Select FLights-->
          <label for="selectFlights">Select Flights</label>
          <div class="row">
            <!-- search autocomplete for flying from -->
            <v-autocomplete
              v-model="flyingFrom"
              :items="airports"
              label="Flying From"
              item-text="name"
              item-value="code"
              return-string="true"
              auto-select-first
              clearable
              dense
              rounded
              class="wid"
              @change="getAirports"
            ></v-autocomplete>
            <v-autocomplete
              v-model="flyingTo"
              :items="airports"
              label="Flying To"
              item-text="name"
              item-value="code"
              return-object
              auto-select-first
              clearable
              dense
              rounded
              class="wid"
              @change="getAirports"
            ></v-autocomplete>
          </div>
        </div>
        <div class="col box">
          <!-- label for Select Travel Dates -->
          <label for="selectTravelDates">Select Travel Dates</label>
          <div class="row">
            <!-- date picker for departure date -->
            <v-menu
              ref="menu"
              v-model="menu"
              :close-on-content-click="false"
              transition="scale-transition"
              offset-y
              min-width="290px"
            >
              <template v-slot:activator="{ on }">
                <v-text-field
                  v-model="departureDate"
                  label="Departure Date"
                  readonly
                  v-on="on"
                  dense
                  rounded
                  class="wid"
                ></v-text-field>
              </template>
              <v-date-picker
                v-model="departureDate"
                no-title
                scrollable
                @input="menu = false"
              ></v-date-picker>
            </v-menu>
            <!-- date picker for return date -->
            <v-menu
              ref="menu"
              v-model="menu"
              :close-on-content-click="false"
              transition="scale-transition"
              offset-y
              min-width="290px"
            >
              <template v-slot:activator="{ on }">
                <v-text-field
                  v-model="returnDate"
                  label="Return Date"
                  readonly
                  v-on="on"
                  dense
                  rounded
                  class="wid"
                ></v-text-field>
              </template>
              <v-date-picker
                v-model="returnDate"
                no-title
                scrollable
                @input="menu = false"
              ></v-date-picker>
            </v-menu>
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
          dense
          rounded
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
      departureDate: null,
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
    };
  },
  methods: {
    hello() {
      // insert values to airports their name of place for airport
      this.airports.insert({ name: "name of place", code: "code of place" });
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
