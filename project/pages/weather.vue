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
      <p id="location" class="text-black">{{ location }}</p>
      <p id="coords" class="text-black text-center">{{ coords }}</p>
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
      location: '',
      coords: '',
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
    // const weather = await this.$axios
    //   .get('https://api.openweathermap.org/data/2.5/weather', {
    //     params: {
    //       lat: lat,
    //       lon: lon,
    //       key: 'd7b7ca5eae3b5be5327aaa4d8d36793d',
    //     },
    //   })
    //   .catch((error) => {
    //     console.log(error)
    //   })
    // this.weather = weather
    // console.log(this.weather)

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
