<template>
  <section>
    <div class="ads-wrapper">
      <h1 class="adsTitle">Target ads to geographic locations</h1>
      <div class="ad Oslo" v-if="basedInOslo">
        <h2>Hold Oslo ren!</h2>
        <p>Besøk elbil-messen 1.januar 2022!</p>
        <img
          class="adImage"
          src="https://images.unsplash.com/photo-1614018991806-950921c7f0fe?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=687&q=80"
          alt="Trikk i Oslobyen"
        />
        <img
          class="adImage"
          src="https://images.unsplash.com/photo-1488161628813-04466f872be2?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=764&q=80"
          alt="Man"
        />
        <p>Ads EV</p>
      </div>

      <div class="ad" v-if="!basedInOslo">
        <h1>Hold Norge rent!</h1>
        <p>Prøv en elbil i dag!</p>
        <img
          class="adImage"
          src="https://images.unsplash.com/photo-1531504060587-e6811129c0f2?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1171&q=80"
          alt="Nordlysbilde"
        />
        <img
          class="adImage"
          src="https://images.unsplash.com/photo-1492446845049-9c50cc313f00?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=687&q=80"
          alt="Skateboarder"
        />
        <p>Ads EV</p>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "GeoAds",
  data() {
    return {
      basedInOslo: true,
      yourLocation: "",
      geoOptions: {
        enableHighAccuracy: true,
        timeout: "Infinity",
        maximumAge: 0,
      },
    };
  },
  methods: {
    runNavigator() {
      navigator.geolocation.getCurrentPosition(
        this.geolocate,
        this.error,
        this.geoOptions
      );
    },
    geolocate(pos) {
      let coordinates = pos.coords;
      let lat = coordinates.latitude;
      let long = coordinates.long;
      if (lat > 59.89 && lat < 59.96 && long > 10.87 && long < 10.66) {
        // if user is within Oslo area
      } else {
        // ....else use is not within Oslo area
        this.basedInOslo = false;
      }
    },
    geoError(error) {
      console.log(error);
    },
  },
  mounted() {
    this.runNavigator();
  },
};
</script>

<style lang="scss" scoped>
h1 {
  font-size: 1rem;
}

.ads-wrapper {
  .adsTitle {
    margin-bottom: 16px;
    color: grey;
  }
  .ad {
    .adImage {
      width: 100%;
      max-height: 200px;
      margin-top: 20px;
      padding: 8px;
      object-fit: cover;
    }
  }
}
</style>
