<template>
  <v-layout row-sm column wrap child-flex-sm>
    <v-flex v-for="market in markets" :key="market.id">
      <v-card hover fluid class="ma-2" id="market-card">
        <v-card-media
          class="white--text"
          height="200px"
          :src="market.image"
        >
          <v-container fill-height fluid class="scrim">
            <v-layout fill-height>
              <v-flex xs12 align-end flexbox>
                <span class="title">{{ market.name }}</span>
              </v-flex>
            </v-layout>
          </v-container>
        </v-card-media>
        <v-card-title>
          <div>
            <span>{{ getHumanOpenHours(market.hours) }}</span><br>
            <span class="grey--text">{{ market.description || "Farmer's Market" }}</span>
          </div>
        </v-card-title>
        <v-card-actions>
          <v-btn flat>Directions</v-btn>
          <div class="rating">
            <v-btn icon>5 <v-icon >star</v-icon></v-btn>
          </div>
        </v-card-actions>
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script>
  import axios from 'axios'
  import moment from 'moment'

  export default {
    data () {
      return {
        markets: []
      }
    },
    mounted () {
      this.getMarkets();
    },
    methods: {
      getMarkets() {
        axios.get('http://localhost:3000/api/v1/markets')
          .then(response => {
              this.markets = response.data;
              return response;
          })
          .catch(error => {
              console.log(error.message);
          });
      },
      getHumanOpenHours(hours) {
        if (hours.length == 1) {
          return hours[0].day_of_week + ' ' + moment(hours[0].open).format("hA") + " - " + moment(hours[0].close).format("hA");
        } else if (hours.length == 7) {
          return 'Daily ' + moment(hours[0].open).format("hA") + " - " + moment(hours[0].close).format("hA");
        } else {
          var dateString = '';

          for(var i = 0; i < hours.length; i++){
            dateString += hours[i].day_of_week + ' ' + moment(hours[i].open).format("hA") + " - " + moment(hours[i].close).format("hA");
            dateString = (i + 1 < hours.length) ? (dateString + ' and ') : dateString;
          }

          return dateString;
        }
      }
    }
  }
</script>
