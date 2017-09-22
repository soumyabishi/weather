<template>
  <div class="hello">


  <!-- {{this.current_conditions.timezone}} -->





  <!-- {{this.current_conditions.hourly.summary}} <br><br> -->


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

          <a href="https://darksky.net/" target="_blank"><img src="../assets/poweredby.png" style="width: 110px;margin-top: 50px;"> </a>
      </div>



  </div>
</template>

<script>




  export default {

    data: function () {
      return {
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

      // Vue loader
      start () {
          this.$Progress.start()
      },
      set (num) {
          this.$Progress.set(num)
      },
      increase (num) {
          this.$Progress.increase(num)
      },
      decrease (num) {
          this.$Progress.decrease(num)
      },
      finish () {
          this.$Progress.finish()
      },
      fail () {
          this.$Progress.fail()
      },



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



        this.$http.get('https://api.darksky.net/forecast/af6ffccfc574f03335a9644c19aa3b3f/' + this.userLat + ',' + this.userLng + '?units=si')
          .then(response => {

              this.current_conditions =  response.body;

          }, error => {
               console.log(failed);

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


</style>
