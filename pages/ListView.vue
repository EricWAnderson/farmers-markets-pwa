<template>
  <v-layout row-sm column wrap>
      <v-card hover class="ma-2 market-card">
        <v-card-media
          class="white--text"
          height="200px"
          src="/static/market-images/mpls-market.png"
        >
          <v-container fill-height fluid class="scrim">
            <v-layout fill-height>
              <v-flex xs12 align-end flexbox>
                <span class="title">Minneapolis Farmers Market</span>
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

      <v-card hover class="ma-2 market-card">
        <v-card-media
          class="white--text"
          height="200px"
          src="/static/market-images/downtown-market.png"
        >
          <v-container fill-height fluid class="scrim">
            <v-layout fill-height>
              <v-flex xs12 align-end flexbox>
                <span class="title">Nicollet Mall Market</span>
              </v-flex>
            </v-layout>
          </v-container>
        </v-card-media>
        <v-card-title>
          <div>
            <span> Thursdays 6am - 6pm</span><br>
            <span class="grey--text">Nicollet Mall downtown</span>
          </div>
        </v-card-title>
        <v-card-actions>
          <v-btn flat>Directions</v-btn>
          <div class="rating">
            <v-btn icon>4 <v-icon >star</v-icon></v-btn>
          </div>
        </v-card-actions>
      </v-card>

      <v-card hover class="ma-2 market-card">
        <v-card-media
          class="white--text"
          height="200px"
          src="/static/market-images/mill-city.png"
        >
          <v-container fill-height fluid class="scrim">
            <v-layout fill-height>
              <v-flex xs12 align-end flexbox>
                <span class="title">Mill City Farmers Market</span>
              </v-flex>
            </v-layout>
          </v-container>
        </v-card-media>
        <v-card-title>
          <div>
            <span> Saturdays 8am - 1pm</span><br>
            <span class="grey--text">Near Guthrie and Mill City Museum</span>
          </div>
        </v-card-title>
        <v-card-actions>
          <v-btn flat>Directions</v-btn>
          <div class="rating">
            <v-btn icon>4 <v-icon >star</v-icon></v-btn>
          </div>
        </v-card-actions>
      </v-card>

      <v-card hover class="ma-2 market-card">
        <v-card-media
          class="white--text"
          height="200px"
          src="/static/market-images/night-market.png"
        >
          <v-container fill-height fluid class="scrim">
            <v-layout fill-height>
              <v-flex xs12 align-end flexbox>
                <span class="title">Mill City Night Market</span>
              </v-flex>
            </v-layout>
          </v-container>
        </v-card-media>
        <v-card-title>
          <div>
            <span> Tuesdays 3:30pm - 7:30pm </span><br>
            <span class="grey--text">Commons near US Bank Stadium</span>
          </div>
        </v-card-title>
        <v-card-actions>
          <v-btn flat>Directions</v-btn>
          <div class="rating">
            <v-btn icon>5 <v-icon >star</v-icon></v-btn>
          </div>
        </v-card-actions>
      </v-card>

      <v-card hover class="ma-2 market-card">
        <v-card-media
          class="white--text"
          height="200px"
          src="/static/market-images/capella-market.png"
        >
          <v-container fill-height fluid class="scrim">
            <v-layout fill-height>
              <v-flex xs12 align-end flexbox>
                <span class="title">Capella Tower Market</span>
              </v-flex>
            </v-layout>
          </v-container>
        </v-card-media>
        <v-card-title>
          <div>
            <span> Wednesdays 11am - 2pm</span><br>
            <span class="grey--text">Downtown in Capella Tower Atrium</span>
          </div>
        </v-card-title>
        <v-card-actions>
          <v-btn flat>Directions</v-btn>
          <div class="rating">
            <v-btn icon>4 <v-icon >star</v-icon></v-btn>
          </div>
        </v-card-actions>
      </v-card>
  </v-layout>
</template>
