<template>
  <div class="hello">


  <!-- {{this.current_conditions.timezone}} -->


    <div v-if="!loading">
              <div class="preloader" style="opacity: 1; ">
                  <svg version="1.1" id="sun" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" width="10px" height="10px" viewBox="0 0 10 10" enable-background="new 0 0 10 10" xml:space="preserve" style="opacity: 1; margin-left: 0px; margin-top: 0px;">
                  <g>
                    <path fill="none" d="M6.942,3.876c-0.4-0.692-1.146-1.123-1.946-1.123c-0.392,0-0.779,0.104-1.121,0.301c-1.072,0.619-1.44,1.994-0.821,3.067C3.454,6.815,4.2,7.245,5,7.245c0.392,0,0.779-0.104,1.121-0.301C6.64,6.644,7.013,6.159,7.167,5.581C7.321,5,7.243,4.396,6.942,3.876z M6.88,5.505C6.745,6.007,6.423,6.427,5.973,6.688C5.676,6.858,5.34,6.948,5,6.948c-0.695,0-1.343-0.373-1.69-0.975C2.774,5.043,3.093,3.849,4.024,3.312C4.32,3.14,4.656,3.05,4.996,3.05c0.695,0,1.342,0.374,1.69,0.975C6.946,4.476,7.015,5,6.88,5.505z"></path>
                    <path fill="none" d="M8.759,2.828C8.718,2.757,8.626,2.732,8.556,2.774L7.345,3.473c-0.07,0.041-0.094,0.132-0.053,0.202C7.319,3.723,7.368,3.75,7.419,3.75c0.025,0,0.053-0.007,0.074-0.02l1.211-0.699C8.774,2.989,8.8,2.899,8.759,2.828z"></path>
                    <path fill="none" d="M1.238,7.171c0.027,0.047,0.077,0.074,0.128,0.074c0.025,0,0.051-0.008,0.074-0.02l1.211-0.699c0.071-0.041,0.095-0.133,0.054-0.203S2.574,6.228,2.503,6.269l-1.21,0.699C1.221,7.009,1.197,7.101,1.238,7.171z"></path>
                    <path fill="none" d="M6.396,2.726c0.052,0,0.102-0.026,0.13-0.075l0.349-0.605C6.915,1.976,6.89,1.885,6.819,1.844c-0.07-0.042-0.162-0.017-0.202,0.054L6.269,2.503C6.228,2.574,6.251,2.666,6.322,2.706C6.346,2.719,6.371,2.726,6.396,2.726z"></path>
                    <path fill="none" d="M3.472,7.347L3.123,7.952c-0.041,0.07-0.017,0.162,0.054,0.203C3.2,8.169,3.226,8.175,3.25,8.175c0.052,0,0.102-0.027,0.129-0.074l0.349-0.605c0.041-0.07,0.017-0.16-0.054-0.203C3.603,7.251,3.513,7.276,3.472,7.347z"></path>
                    <path fill="none" d="M3.601,2.726c0.025,0,0.051-0.007,0.074-0.02C3.746,2.666,3.77,2.574,3.729,2.503l-0.35-0.604C3.338,1.828,3.248,1.804,3.177,1.844C3.106,1.886,3.082,1.976,3.123,2.047l0.35,0.604C3.5,2.7,3.549,2.726,3.601,2.726z"></path>
                    <path fill="none" d="M6.321,7.292c-0.07,0.043-0.094,0.133-0.054,0.203l0.351,0.605c0.026,0.047,0.076,0.074,0.127,0.074c0.025,0,0.051-0.006,0.074-0.02c0.072-0.041,0.096-0.133,0.055-0.203l-0.35-0.605C6.483,7.276,6.393,7.253,6.321,7.292z"></path>
                    <path fill="none" d="M2.202,5.146c0.082,0,0.149-0.065,0.149-0.147S2.284,4.851,2.202,4.851H1.503c-0.082,0-0.148,0.066-0.148,0.148s0.066,0.147,0.148,0.147H2.202z"></path>
                    <path fill="none" d="M8.493,4.851H7.794c-0.082,0-0.148,0.066-0.148,0.148s0.066,0.147,0.148,0.147l0,0h0.699c0.082,0,0.148-0.065,0.148-0.147S8.575,4.851,8.493,4.851L8.493,4.851z"></path>
                    <path fill="none" d="M5.146,2.203V0.805c0-0.082-0.066-0.148-0.148-0.148c-0.082,0-0.148,0.066-0.148,0.148v1.398c0,0.082,0.066,0.149,0.148,0.149C5.08,2.352,5.146,2.285,5.146,2.203z"></path>
                    <path fill="none" d="M4.85,7.796v1.396c0,0.082,0.066,0.15,0.148,0.15c0.082,0,0.148-0.068,0.148-0.15V7.796c0-0.082-0.066-0.148-0.148-0.148C4.917,7.647,4.85,7.714,4.85,7.796z"></path>
                    <path fill="none" d="M2.651,3.473L1.44,2.774C1.369,2.732,1.279,2.757,1.238,2.828C1.197,2.899,1.221,2.989,1.292,3.031l1.21,0.699c0.023,0.013,0.049,0.02,0.074,0.02c0.051,0,0.101-0.026,0.129-0.075C2.747,3.604,2.722,3.514,2.651,3.473z"></path>
                    <path fill="none" d="M8.704,6.968L7.493,6.269c-0.07-0.041-0.162-0.016-0.201,0.055c-0.041,0.07-0.018,0.162,0.053,0.203l1.211,0.699c0.023,0.012,0.049,0.02,0.074,0.02c0.051,0,0.102-0.027,0.129-0.074C8.8,7.101,8.776,7.009,8.704,6.968z"></path>
                  </g>
                  </svg>

                  <svg version="1.1" id="cloud" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" width="10px" height="10px" viewBox="0 0 10 10" enable-background="new 0 0 10 10" xml:space="preserve">
                  <path fill="none" d="M8.528,5.624H8.247c-0.085,0-0.156-0.068-0.156-0.154c0-0.694-0.563-1.257-1.257-1.257c-0.098,0-0.197,0.013-0.3,0.038C6.493,4.259,6.45,4.252,6.415,4.229C6.38,4.208,6.356,4.172,6.348,4.131C6.117,3.032,5.135,2.235,4.01,2.235c-1.252,0-2.297,0.979-2.379,2.23c-0.004,0.056-0.039,0.108-0.093,0.13C1.076,4.793,0.776,5.249,0.776,5.752c0,0.693,0.564,1.257,1.257,1.257h6.495c0.383,0,0.695-0.31,0.695-0.692S8.911,5.624,8.528,5.624z"></path>
                  </svg>

                  <div class="rain">
                  <span class="drop"></span>
                  <span class="drop"></span>
                  <span class="drop"></span>
                  <span class="drop"></span>
                  <span class="drop"></span>
                  <span class="drop"></span>
                  <span class="drop"></span>
                  <span class="drop"></span>
                  <span class="drop"></span>
                  <span class="drop"></span>
                  </div>

                  <div class="text">
                  LOOKING OUTSIDE FOR YOU... ONE SEC
                  </div>
         </div>
    </div>


  <!-- {{this.current_conditions.hourly.summary}} <br><br> -->

   <div v-if="loading">
      <section class="sectionone">

          <!--logo section starts here-->
          <div class="ui container logo">

              <p>Climate. </p>
          </div>


          <div class="ui container">
          <div class="ui grid">


              <div class="seven wide column">
                  <div class="ui grid">
                      <div class="eight wide column climateimage">

                              <img src="../assets/sunny.svg">

                      </div>

                      <div class="eight wide column celcius">

                          <h2 class="temperature">{{this.current_conditions.currently.temperature}}° C</h2>
                          <p class="weathercondition">{{this.current_conditions.currently.summary}}</p>
                          <i class="lastupdate">Last updated at 5 minutes ago </i>
                      </div>

                  </div>


              </div>
              <div class="nine wide column location">
                  <h2 class="city">Hyderabad</h2>
                  <p class="date">Wed, &nbsp;20th Sept 2017</p>
              </div>




          </div>


           <h3>

               <span style="    display: inline-block;
    font-size: 10px;
    background: rgb(255, 255, 255);
    color: #3875a5;
    text-transform: uppercase;
    padding: 3px 17px;
    border-radius: 87px;
    font-weight: 600;
    letter-spacing: 2px;
    margin-bottom: 12px;">forecast</span> <br>{{this.current_conditions.hourly.summary}}</h3>
           </div>

      </section>

      <section>

          <div class="ui container">
              <div class="ui three column grid sectiontwo">

                  <div class="column">
                      <div class="ui middle aligned grid">
                          <div class="eight wide right aligned column">
                              <img src="../assets//humid.svg" style="width: 105px;">
                          </div>

                          <div class="eight wide column humid">
                              <p class="pheading">{{this.current_conditions.currently.humidity}}</p>
                              <p class="psubheading">Humidity</p>
                          </div>

                      </div>
                  </div>

                  <div class="column">
                      <div class="ui middle aligned grid">
                          <div class="eight wide right aligned column">
                              <img src="../assets//wind.svg" style="width: 105px;">
                          </div>

                          <div class="eight wide column humid">
                              <p class="pheading">{{this.current_conditions.currently.windSpeed}} m/s</p>
                              <p class="psubheading"> Wind speed</p>
                          </div>

                      </div>
                  </div>
                  <div class="column">
                      <div class="ui middle aligned grid">
                          <div class="eight wide right aligned column">
                              <img src="../assets/pressure.svg" style="width: 105px;">
                          </div>

                          <div class="eight wide column humid">
                              <p class="pheading">{{this.current_conditions.currently.pressure}} hPa</p>
                              <p class="psubheading">Pressure</p>
                          </div>

                      </div>
                  </div>

              </div>
          </div>
      </section>




      <div class="ui center aligned container">

          <a href="https://darksky.net/" target="_blank"><img src="../assets/poweredby.png" style="width: 110px;margin-top: 70px;    margin-bottom: 100px;"> </a>
      </div>

   </div>



  </div>
</template>

<script>




  export default {

    data: function () {
      return {
        loading: false,
        userLat: '',
        userLng: '',
        current_conditions :{
            timezone :'',
            currently : [
               {

                 summary :'',
                 temperature :'',
                 icon :'',
                 humidity:'',
                 pressure:'',

               }
            ],

            hourly : [

                 {
                   summary :'',
                 }


            ]
        }
      }
    },

    methods: {




      askGeolocation() {
        // check if browser support geolocation


        if (navigator.geolocation) {
          // ask permission and take positions

          var setLatLong = '';
          var error = '';
          var options= '';
          // navigator.geolocation.getCurrentPosition(setLatLong);
          navigator.geolocation.getCurrentPosition(this.setLatLong,this.location_fetch_error);


        } else {
          alert("Geolocation is not supported by your browser.");
        }
      },

      location_fetch_error() {

        alert("Error fetching your location");

      },

      setLatLong(position) {
        // save position
        this.userLat = position.coords.latitude;
        this.userLng = position.coords.longitude;

        // this.fetch_location_key();
        this.fetch_current_conditions();
      },


     // Get location key
      // fetch_location_key() {
      //
      //   this.$http.get('http://dataservice.accuweather.com/locations/v1/cities/geoposition/search?apikey=Fms1WxFTkuMCye03ASfvjREBoKJ953is&q=' + this.userLat  + '%2C' + this.userLng)
      //     .then(response => {
      //       this.location_key = response.body.Key;
      //     }, error => {
      //          console.log(failed)
      //     });
      // },

      // Get Current weather condition
      fetch_current_conditions(){


        this.loading = true;


        this.$Progress.start()

        this.$http.get('https://api.darksky.net/forecast/af6ffccfc574f03335a9644c19aa3b3f/' + this.userLat + ',' + this.userLng + '?units=si')
          .then(response => {

              this.current_conditions =  response.body;
                this.$Progress.finish()

          }, error => {
               console.log(failed);
                 this.$Progress.fail()

          });

      }


    },


    mounted: function() {
      this.askGeolocation();
    }


  }


</script>




<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>

@import "../assets/semantic.min.css";


.logo {

    padding-top: 37px;
    color: white;
    font-size: 33px!important;
    font-weight: 600;
}

.sectionone {
    background: #36D1DC;  /* fallback for old browsers */
    background: -webkit-linear-gradient(to right, #5B86E5, #36D1DC);  /* Chrome 10-25, Safari 5.1-6 */
    background: linear-gradient(to right, #5B86E5, #36D1DC); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */

    min-height: 523px;
}

.sectiontwo {
    margin-top: 40px !important;
}

.climateimage {
    margin-top: 72px;
}

.celcius {

    margin-top: 109px;
}

.location {
    margin-top: 113px;
    padding-left: 50px !important;
}


.pheading {
    font-size: 28px;
    margin-bottom: 0;
}

.psubheading {
    color: #777777;
    font-size: 16px;
    margin-top: 2px;
}

.humid {
    padding-top: 44px !important;
    padding-bottom: 44px !important;
}

.temperature {
    font-size: 54px;
    color: #ffffff;
    margin-bottom: 0;
}

.weathercondition {

    font-size: 24px;
    color: #ffffff;
    opacity: 0.5;
    margin-bottom: 0;

}

.lastupdate {
  font-size: 12px;
color: #ffffff;
opacity: 0.5;
margin-top: 7px;
display: block;
}

.city {
  font-size: 54px;
color: #ffffff;
margin-bottom: 5px;
margin-top: -5px !important;
}

.time {
    font-size: 21px;
    color: #ffffff;
    margin-bottom: 0;
    margin-top: 21px;
    opacity: 0.5;
}

.date {
    font-size: 21px;
    color: white;
    opacity: 0.5;
}


h3{
  color: rgb(255, 255, 255);
font-weight: 300;
font-size: 18px;
margin-left: 250px;
max-width: 450px;
line-height: 1.7;
padding-bottom: 100px;
}




.preloader {
	position: absolute;
	margin-left: -55px;
	margin-top: -100px;
	height: 110px;
	width: 110px;
	left: 50%;
	top: 50%;
}

svg {
  width: 110px;
  height: 110px;
}

path {
  stroke: #9ea1a4;
  stroke-width: 0.25;
  fill: #241E20;
}

#cloud {
  position: relative;
  z-index: 2;
}

#cloud path {
  fill: #efefef;
}

#sun {
  margin-left: -10px;
  margin-top: 6px;
  opacity: 0;
  width: 60px;
  height: 60px;
  position: absolute;
  left: 45px;
  top: 15px;
  z-index: 1;

  animation-name: rotate;
  animation-duration: 16000ms;
  animation-iteration-count: infinite;
  animation-timing-function: linear;
}

#sun path {
  stroke-width: 0.18;
  fill: #9ea1a4;
}


@keyframes rotate {
  0% {
    transform: rotateZ(0deg);
  }

  100% {
    transform: rotateZ(360deg);
  }
}

/* Rain */
.rain {
  position: absolute;
  width: 70px;
  height: 70px;
  margin-top: -32px;
  margin-left: 19px;
}

.drop {
  opacity: 1;
  background: #9ea1a4;
  display: block;
  float: left;
  width: 3px;
  height: 10px;
  margin-left: 4px;
  border-radius: 0px 0px 6px 6px;

  animation-name: drop;
  animation-duration: 350ms;
  animation-iteration-count: infinite;
}

.drop:nth-child(1) {
  animation-delay: -130ms;
}

.drop:nth-child(2) {
  animation-delay: -240ms;
}

.drop:nth-child(3) {
  animation-delay: -390ms;
}

.drop:nth-child(4) {
  animation-delay: -525ms;
}

.drop:nth-child(5) {
  animation-delay: -640ms;
}

.drop:nth-child(6) {
  animation-delay: -790ms;
}

.drop:nth-child(7) {
  animation-delay: -900ms;
}

.drop:nth-child(8) {
  animation-delay: -1050ms;
}

.drop:nth-child(9) {
  animation-delay: -1130ms;
}

.drop:nth-child(10) {
  animation-delay: -1300ms;
}


@keyframes drop {
  50% {
    height: 45px;
    opacity: 0;
  }

  51% {
    opacity: 0;
  }

  100% {
    height: 1px;
    opacity: 0;
  }
}

.text {
	font-family: Helvetica, 'Helvetica Neue', sans-serif;
	letter-spacing: 1px;
	text-align: center;
	margin-left: -43px;
	font-weight: bold;
	margin-top: 20px;
	font-size: 11px;
	color: #a0a0a0;
	width: 200px;
}


</style>
