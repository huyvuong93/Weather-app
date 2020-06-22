<template>
  <div class="hello">
    <input type="text" v-model="selectValue" class="search_bar" placeholder="Name the city" @keypress="showWeather">
    <h1>{{ message }}</h1>
    <div class="box">
    <div class="clock">
      <p class="time" v-text="time"></p>
    </div> 
    <div class="weather">
      <p class="weather_city">{{ city }}</p>
      <p class="weather_city">{{ temp }}</p>
      <p class="weather_city">{{ condition.main }}</p>
    </div>
    </div>
  </div>
</template>

<script>
import moment from 'moment'

export default {
  data () {
    return{
      message: "Hi Vuong",
      time:null ,
      selectValue: '',
      city:'',
      temp: '',
      condition:{
        main:'',    
      }
    }
  },
  methods:{
    showWeather(){
        let apiURL = 'https://api.openweathermap.org/data/2.5/forecast?q=' + this.selectValue + ',jp&units=metric&lang=ja&APPID=6feb96feab4f7959cbc8ee732f5cdf79'
        this.axios.get(apiURL).then(function(response){
          this.city = this.selectValue
          this.temp = response.data.list[0].main.temp
          this.condition.main= response.data.list[0].weather[0].main
          console.log(this.condition.main)
          console.log(response)
        }.bind(this)).catch(function(error){
          console.log('Error'+ error)
        })
    },
    updatetime () {
      this.time = moment().format('LTS')
      }
    },
    created () {
      this.time = moment().format('LTS');
      setInterval(() => this.updatetime(), 1 * 1000);
  },
    
  }

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}

.clock{
  width: 100%;
  height: 100%;
}
.box{
  padding: 150px 5% 100px;
}
.hello h1{
  font-size: 60px;
  margin-top:30px;
}
.hello p{
  font-size: 40px;
  margin-bottom: 0;
}
.hello{
  width: 100%;
  height: 93vh;
  color:white;

}
.hello{
  background-image: url("https://i.ytimg.com/vi/LWt6Cg9Wqw4/maxresdefault.jpg");
  background-position-x: center;
  background-size:cover ;
  background-repeat: no-repeat;
}
.search_bar{
  display: block;
  width: 100%;
  padding: 15px;
  background-color: rgba(255,255,255,0.5);
  color:#313131;
}
</style>
