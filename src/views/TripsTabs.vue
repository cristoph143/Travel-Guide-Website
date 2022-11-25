<template>
  <div class="trips tabs">
    <form class="trips">
      <div class="center row">
        <div class="col box">
          <label for="selectLocations">Select Starting Locations</label>
          <div class="row">
            <v-autocomplete
              v-model="startingLocation"
              :items="locations"
              label="Philippines, any Location"
              item-text="name"
              item-value="code"
              return-string="true"
              auto-select-first
              clearable
              dense
              rounded
              class="wid"
              @change="getLocation"
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
    </form>
  </div>
</template>

<script>
export default {};
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
