<template>
  <div class="hotels tabs">
    <form class="hotels">
      <div class="center row">
        <div class="col boxes">
          <label for="selectDestinations">Select Destinations</label>
          <div class="row">
            <v-autocomplete
              v-model="startingDestination"
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
              @change="getDestination"
            ></v-autocomplete>
          </div>
        </div>
        <div class="col boxes">
          <!-- label for Select dates -->
          <label for="selectTravelDates">Select Travel Dates</label>
          <div class="row">
            <!-- date picker for checkin date -->
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
                  v-model="checkinDate"
                  label="Checkin Date"
                  readonly
                  v-on="on"
                  dense
                  rounded
                  class="wid"
                ></v-text-field>
              </template>
              <v-date-picker
                v-model="checkinDate"
                no-title
                scrollable
                @input="menu = false"
              ></v-date-picker>
            </v-menu>
            <!-- date picker for checkout date -->
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
                  v-model="checkoutDate"
                  label="Checkout Date"
                  readonly
                  v-on="on"
                  dense
                  rounded
                  class="wid"
                ></v-text-field>
              </template>
              <v-date-picker
                v-model="checkoutDate"
                no-title
                scrollable
                @input="menu = false"
              ></v-date-picker>
            </v-menu>
          </div>
        </div>
        <div class="col boxes">
          <!-- label for guest -->
          <label for="selectGuest">Guest</label>
          <div class="guest row">
            <!-- number of guest and  number of rooms -->
            <v-text-field
              v-model="guest"
              label="Guest"
              dense
              rounded
              class="wid"
            ></v-text-field>
            <v-text-field
              v-model="rooms"
              label="Rooms"
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
.boxes {
  width: 276px;
  margin-right: 15px;
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
