<template>
  <div
    id="weatherApp"
    class="h-screen flex flex-col justify-center items-center"
  >
    <home-link class="hover:text-blue-300" />
    <h1 class="text-4xl text-blue-300">Weather</h1>
    <div
      id="app"
      class="w-64 h-64 mt-4 bg-blue-200 rounded-xl flex flex-col justify-center items-center"
    >
      <h2 id="temp" class="text-4xl text-black">{{ currentTemp }}</h2>
      <h3 id="weather" class="text-2xl text-black">{{ currentWeather }}</h3>
      <p id="location" class="text-lg text-black">{{ location }}</p>
    </div>
  </div>
</template>

<script>
// get location of user using built in geolocation function
// use geocode api to get location from lat, long
// use weather api to get weather of user's current location
// use autocomplete location api for location autocomplete
// use geocode api to change location to lat, long
// use weather api to get weather of location

export default {
  name: 'WeatherApp',
  data() {
    return {
      currentTemp: '',
      currentWeather: '',
      location: '',
    }
  },
  async created() {
    // getting user's current location on load
    // navigator.geolocation.getCurrentPosition(getLocation)
    // function getLocation(position, error) {
    //   if (navigator.geolocation) {
    //     let latlng = `${position.coords.latitude},${position.coords.longitude}`
    //     console.log(latlng)
    //     return latlng
    //   } else {
    //     console.log(error)
    //   }
    // }

    // converting user's lat long to location
    let lat = '40.5982987'
    let lon = '-73.9898438'
    let latlng = `${lat},${lon}`
    // let latlng = await this.getLocation
    const readAddress = await this.$axios
      .get('https://maps.googleapis.com/maps/api/geocode/json', {
        params: {
          latlng: latlng,
          key: 'AIzaSyBJckpIv5OIPM2LNtKoZnbZ3l9kw7iptxc',
        },
      })
      .catch((error) => {
        console.log(error)
      })
    this.readAddress = readAddress
    // console.log(this.readAddress.data)
    this.location = this.readAddress.data.results[5].formatted_address
    console.log(this.location)

    // get weather data of location
    const getWeather = await this.$axios
      .get('https://api.openweathermap.org/data/2.5/weather', {
        params: {
          lat: lat,
          lon: lon,
          appid: '92cd362c6a149d5b565332af16b11818',
        },
      })
      .catch((error) => {
        console.log(error)
      })
    this.getWeather = getWeather.data
    console.log(this.getWeather)
    this.temp = getWeather.data.main.temp
    // this.temp = this.temp - 273.15
    // this.temp = this.temp * 1.8 + 32
    this.currentTemp = `${
      Math.round(((this.temp - 273.15) * 1.8 + 32 + Number.EPSILON) * 1) / 1
    }°`
    console.log(this.currentTemp)
    this.currentWeather = getWeather.data.weather[0].main
    console.log(this.currentWeather)

    // address to lat long
    let address = 'Brooklyn, NY, USA'
    const getCoords = await this.$axios
      .get('https://maps.googleapis.com/maps/api/geocode/json', {
        params: {
          address: address,
          key: 'AIzaSyBJckpIv5OIPM2LNtKoZnbZ3l9kw7iptxc',
        },
      })
      .catch((error) => {
        console.log(error)
      })
    this.getCoords = getCoords
    // console.log(this.getCoords.data)
    this.coords = `${this.getCoords.data.results[0].geometry.location.lat},${this.getCoords.data.results[0].geometry.location.lng}`
    console.log(this.coords)
  },

  methods: {},
}
</script>
