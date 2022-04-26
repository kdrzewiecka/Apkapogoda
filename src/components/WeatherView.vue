<template>
   <div class="weatherView">
  <h1>Weather</h1>
   
  
   <div class="cityPicker">
       <input type="text" v-model="cityName">
       <button @click="getLocation">Szukaj</button>
   </div>
   
   
   <table>
       <tr>
           <th>City</th>
           <td>{{currentName}}</td>
       </tr>
       <tr>
           <th>LAT</th>
           <td>{{lat}}</td>
       </tr>
       <tr>
           <th>LON</th>
           <td>{{lon}}</td>
       </tr>
   </table>




   </div>


</template>

<script>
export default {
    name:"WeatherView",
    data(){
      return{
         // weather: "sun",
         cityName: "Gdańsk",
         lat: "",
         lon: "",
         currentCity: ""
         
      }
    },
    methods:{
        getWeather(){
            console.log('getWeather');


        },
        getLocation(cityName){
            console.log(cityName)

            fetch("http://api.openweathermap.org/geo/1.0/direct?q="+cityName+"&appid=04d03c358e8933ac6823da54c340c97b")
             .then(dt => dt.json())
             .then(dt => {
                 this.cityName = dt[0].name;
                 this.currentCity = dt[0].name;
                 this.lat = dt[0].lat;
                 this.lon = dt[0].lon;
                 console.log(dt[0])
          })
        }
    },
    created(){
        this.getLocation();
    }

}
</script>

<style>

</style> 