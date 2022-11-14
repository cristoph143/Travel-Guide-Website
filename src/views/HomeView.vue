<template>
  <div class="home">
    <div class="booking">
      <h>Welcome to the Philippines</h>
      <p>Book your next trip to the Philippines</p>
      <div class="boxes">
        <div class="radios">
          <div class="header_div">
            <!-- button for flights -->
            <input
              type="radio"
              id="flight"
              name="booking"
              value="flight"
              v-model="bookingType"
              @click="setBookingType('flight')"
            />
            <label for="flight">Flights</label>
          </div>
          <div class="header_div">
            <!-- button for hotels -->
            <input
              type="radio"
              id="hotel"
              name="booking"
              value="hotel"
              v-model="bookingType"
              @click="setBookingType('hotel')"
            />
            <label for="hotel">Hotels</label>
          </div>
        </div>
        <!-- when setbookingtype is flight then show this div -->
        <div v-if="bookingType === 'flight'" class="template">
          <div class="flight">
            <div class="flight-from col">
              <label for="flight-from">From</label>
              <input
                type="text"
                id="flight-from"
                name="flight-from"
                placeholder="Enter a city or airport"
                v-model="flightFrom"
              />
            </div>
            <div class="flight-to col">
              <label for="flight-to">To</label>
              <input
                type="text"
                id="flight-to"
                name="flight-to"
                placeholder="Enter a city or airport"
                v-model="flightTo"
              />
            </div>
            <div class="flight-date col">
              <label for="flight-date">Departure Date</label>
              <input
                type="date"
                id="flight-date"
                name="flight-date"
                v-model="flightDate"
              />
            </div>
            <!-- return date -->
            <div class="flight-return-date col">
              <label for="flight-return-date">Return Date</label>
              <input
                type="date"
                id="flight-return-date"
                name="flight-return-date"
                v-model="flightReturnDate"
              />
            </div>
            <!-- dropdown for list of passengers with increment decrement value -->
            <div class="flight-passengers col">
              <label for="flight-passengers">Passengers</label>
              <select
                name="flight-passengers"
                id="flight-passengers"
                v-model="flightPassengers"
              >
                <!-- default option to be display -->
                <option value="0" disabled selected>Choose</option>
                <option
                  v-for="passenger in passengers"
                  :value="passenger"
                  :key="passenger"
                >
                  {{ passenger }}
                  <div class="passenger">
                    <div class="passenger-adults">
                      <label for="passenger-adults">Adults</label>
                      <div class="passenger-adults-input">
                        <input
                          type="number"
                          id="passenger-adults"
                          name="passenger-adults"
                          min="1"
                          max="9"
                          v-model="passengerAdults"
                        />
                      </div>
                    </div>
                    <div class="passenger-children">
                      <label for="passenger-children">Children</label>
                      <div class="passenger-children-input">
                        <input
                          type="number"
                          id="passenger-children"
                          name="passenger-children"
                          min="0"
                          max="9"
                          v-model="passengerChildren"
                        />
                      </div>
                    </div>
                    <div class="passenger-infants">
                      <label for="passenger-infants">Infants</label>
                      <div class="passenger-infants-input">
                        <input
                          type="number"
                          id="passenger-infants"
                          name="passenger-infants"
                          min="0"
                          max="9"
                          v-model="passengerInfants"
                        />
                      </div>
                    </div>
                  </div>
                  <!-- add a section of each passenger to add or decrease number of passenger -->
                  <button
                    class="passenger-button"
                    @click="decrementPassengers"
                    :disabled="flightPassengers === 1"
                  >
                    -
                  </button>
                  <!-- input for number of passenger and it can display flightPassengers -->
                  <input
                    type="text"
                    class="passenger-input"
                    :value="flightPassengers"
                  />
                  <button
                    class="passenger-button"
                    @click="incrementPassengers"
                    :disabled="flightPassengers === 9"
                  >
                    +
                  </button>
                </option>
              </select>
            </div>
            <div class="flight-submit">
              <button @click="searchFlight">Search</button>
            </div>
          </div>
          <div class="flight down">
            <!-- dropdown for roundtrip or oneway -->
            <div class="flight-type left col">
              <select id="flight-type" name="flight-type" v-model="flightType">
                <option value="roundtrip">Roundtrip</option>
                <option value="oneway">One Way</option>
              </select>
            </div>
            <div class="flight-class left col">
              <select
                id="flight-class"
                name="flight-class"
                v-model="flightClass"
              >
                <option value="economy">Economy</option>
                <option value="business">Business</option>
                <option value="first">First</option>
              </select>
            </div>
          </div>
        </div>
        <!-- when setbookingtype is hotel then show this div -->
        <div v-if="bookingType === 'hotel'" class="template">
          <div class="hotel">
            <div class="hotel-location">
              <label for="hotel-location">Location</label>
              <input
                type="text"
                id="hotel-location"
                name="hotel-location"
                placeholder="Enter a city or airport"
                v-model="hotelLocation"
              />
            </div>
            <div class="hotel-checkin">
              <label for="hotel-checkin">Check-in</label>
              <input
                type="date"
                id="hotel-checkin"
                name="hotel-checkin"
                v-model="hotelCheckin"
              />
            </div>
            <div class="hotel-checkout">
              <label for="hotel-checkout">Check-out</label>
              <input
                type="date"
                id="hotel-checkout"
                name="hotel-checkout"
                v-model="hotelCheckout"
              />
            </div>
            <div class="hotel-guests">
              <label for="hotel-guests">Guests</label>
              <input
                type="number"
                id="hotel-guests"
                name="hotel-guests"
                min="1"
                max="10"
                v-model="hotelGuests"
              />
            </div>
            <div class="hotel-submit">
              <button @click="searchHotel">Search</button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HomeView",
  data() {
    return {
      bookingType: "flight",
      flightFrom: "",
      flightTo: "",
      flightDate: "",
      flightReturnDate: "",
      flightPassengers: 1,
      flightClass: "economy",
      flightType: "roundtrip",
      hotelLocation: "",
      hotelCheckin: "",
      hotelCheckout: "",
      hotelGuests: 1,
      passengers: ["adult", "children", "infant"],
      num_passengers: 1,
    };
  },
  methods: {
    setBookingType(type) {
      this.bookingType = type;
    },
    searchFlight() {
      this.$router.push({
        name: "flights",
        params: {
          from: this.flightFrom,
          to: this.flightTo,
          date: this.flightDate,
          returnDate: this.flightReturnDate,
          passengers: this.flightPassengers,
          class: this.flightClass,
          type: this.flightType,
        },
      });
    },
    searchHotel() {
      this.$router.push({
        name: "hotels",
        params: {
          location: this.hotelLocation,
          checkin: this.hotelCheckin,
          checkout: this.hotelCheckout,
          guests: this.hotelGuests,
        },
      });
    },
    incrementPassengers() {
      this.flightPassengers++;
    },
    decrementPassengers() {
      this.flightPassengers--;
    },
  },
};
</script>

<style scoped>
.booking {
  background: url("./../assets/background-place.jpg");
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  height: 60vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  color: white;
}
.flights {
  display: flex;
  align-items: center;
  margin: 10px;
  display: none;
}
.radios {
  display: flex;
  align-items: center;
}
.radios input {
  margin: 0 10px;
}
.radios input:checked + .radio {
  background-color: blue;
}
input[type="radio"] {
  display: none;
}
/* input type radio that is not active set bgcolor to white */
input[type="radio"]:checked:after {
  background-color: white;
}
.booking-type {
  display: flex;
  align-items: center;
  margin: 10px;
}
.booking-type input {
  margin: 0 10px;
}
.flight {
  display: flex;
  align-items: center;
  margin: 10px;
}
.flight input {
  margin: 0 10px;
}
.flight-submit {
  margin: 10px;
  display: flex;
  align-items: center;
}
.col {
  display: flex;
  flex-direction: column;
  align-items: baseline;
}
.template {
  display: flex;
  justify-content: center;
  align-items: baseline;
  height: 20vh;
  background-color: blue;
  opacity: 0.7;
  flex-direction: column;
  width: 1000px;
}
.left {
  margin-left: 20px;
}
.passenger {
  display: flex;
  align-items: center;
  margin: 10px;
}
.header_div {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-right: 50px;
  background-color: blue;
  width: 200px;
  height: 40px;
}
</style>
