<template>
  <v-layout row-sm column wrap>
    <v-flex v-for="market in markets" :key="market.id">
      <v-container grid-list-xs>
        <v-menu
          transition="slide-y-transition"
          bottom
          right
          full-width
        >
          <!-- front side of card -->
          <v-card tile hover fluid id="market-card" class="md-1" slot="activator">
            <v-card-media
              class="white--text"
              height="200px"
              :src="market.image"
            >
              <v-container fill-height fluid class="scrim">
                <v-layout fill-height>
                  <v-flex xs12 align-end flexbox>
                    <span class="title">{{ market.name }}</span><br>
                  </v-flex>
                </v-layout>
              </v-container>
            </v-card-media>
            <v-card-title>
              <div>
                <span>{{ getHumanOpenHours(market.hours) }}</span><br>
                <span class="grey--text">{{ market.description || "Farmer's Market" }}</span>
              </div>
              <div class="directions">
                <a :href="'http://www.google.com/maps/place/' + market.address.latitude + ',' + market.address.longitude"><v-btn icon><v-icon >directions</v-icon></v-btn></a>
              </div>
            </v-card-title>
          </v-card>

          <!-- back side of card -->
          <v-card tile height="274px">
            <v-list dense>
              <v-list-tile>
                <v-list-tile-title>
                  <v-list-tile-title class="title">{{ market.name }}</v-list-tile-title>
                </v-list-tile-title>
                <v-list-action>
                  <v-icon class="indigo--text">close</v-icon>
                </v-list-action>
              </v-list-tile>
              <v-list-tile v-if="market.url">
                <v-list-tile-action>
                  <v-icon class="indigo--text">public</v-icon>
                </v-list-tile-action>
                <v-list-tile-content>
                  <v-list-tile-title class="max-width">{{ market.url }}</v-list-tile-title>
                </v-list-tile-content>
              </v-list-tile>
              <v-list-tile v-if="market.phone">
                <v-list-tile-action>
                  <v-icon class="indigo--text">phone</v-icon>
                </v-list-tile-action>
                <v-list-tile-content>
                  <v-list-tile-title class="max-width">{{ market.phone }}</v-list-tile-title>
                </v-list-tile-content>
              </v-list-tile>
              <v-list-tile v-if="market.email">
                <v-list-tile-action>
                  <v-icon class="indigo--text">mail</v-icon>
                </v-list-tile-action>
                <v-list-tile-content>
                  <v-list-tile-title class="max-width">{{ market.email }}</v-list-tile-title>
                </v-list-tile-content>
              </v-list-tile>
              <v-list-tile v-if="market.address">
                <v-list-tile-action>
                  <v-icon class="indigo--text">location_on</v-icon>
                </v-list-tile-action>
                <v-list-tile-content class="max-width">
                  <v-list-tile-title>{{ market.address.street }}</v-list-tile-title>
                  <v-list-tile-sub-title>{{ market.address.city }}, {{ market.address.state }} {{ market.address.zip }}</v-list-tile-sub-title>
                </v-list-tile-content>
              </v-list-tile>
            </v-list>
          </v-card>
        </v-menu>
      </v-container>
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
