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
      <p id="location"></p>
    </div>
  </div>
</template>

<script>
// use geocode api to get location from lat, lon
// use autocomplete location api for location autocomplete
// use geocode api to change location to lat, lon
// use weather api to get weather of location

export default {
  name: 'WeatherApp',
  data() {
    return {
      key: 'AIzaSyBJckpIv5OIPM2LNtKoZnbZ3l9kw7iptxc',
    }
  },
  created() {
    // getting user's current location on load
    navigator.geolocation.getCurrentPosition(getLocation)
    function getLocation(position, error) {
      if (navigator.geolocation) {
        let lat = position.coords.latitude
        let lng = position.coords.longitude
        const latlng = `${lat},${lng}`
        console.log(latlng)
      } else {
        console.log(error)
      }
    }

    function getGeocode() {
      let latlng = '40.5982922,-73.9898245'
      axios
        .get('https://maps.googleapis.com/maps/api/geocode/json', {
          params: {
            latlng: latlng,
            key: 'AIzaSyBJckpIv5OIPM2LNtKoZnbZ3l9kw7iptxc',
          },
        })
        .then((response) => {
          console.log(response)
        })
        .catch((error) => {
          console.log(error)
        })
    }
    getGeocode()
  },
  methods: {},
}
</script>
