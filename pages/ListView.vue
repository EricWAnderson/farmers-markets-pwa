<template>
  <v-layout row-sm column wrap>
      <v-card hover class="ma-2 market-card" v-for="market in markets">
        <v-card-media
          class="white--text"
          height="200px"
          src="/static/market-images/mpls-market.png"
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
            <span> Daily 6am - 1pm</span><br>
            <span class="grey--text">Largest market. Near I-94 & Hwy 55</span>
          </div>
        </v-card-title>
        <v-card-actions>
          <v-btn flat>Directions</v-btn>
          <div class="rating">
            <v-btn icon>5 <v-icon >star</v-icon></v-btn>
          </div>
        </v-card-actions>
      </v-card>
  </v-layout>
</template>

<script>
  import axios from 'axios'

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
      }
    }
  }
</script>
