<template>
  <v-app>
    <main v-if="!loading">
      <DataTitle :text="title" :dataDate="dataDate"></DataTitle>
      <DataBoxes :status="status"></DataBoxes>
      <CountrySelect :countries="countries" @get-country="getCountryData"></CountrySelect>
  
      <v-btn @click="ClearCountry()" v-if="status.Country"  :style="{bottom:'10%' ,left: '34.4%'}" rounded
        outlined large color="green"  class=" white--text pa-3 mt-10">
        Clear Country
      </v-btn>
    </main>
    <main class="flex flex-column  align-center justify-center text-center" v-else>
      <div class=" grey--text text-md-h5 mt-10 mb-6">
        Fetching Data
      </div>
      <img :src="loadingImage" class="w-24 m-auto" alt=" " />
    </main>
  </v-app>
</template>

<script>
import DataTitle from '@/components/DataTitle.vue';
import DataBoxes from '@/components/DataBoxes.vue';
import CountrySelect from '@/components/CountrySelect.vue';

export default {
  name: "Home_View",
  components: { DataTitle, DataBoxes, CountrySelect },
  data() {
    return {
      loading: true,
      title: "Global",
      dataDate: "",
      status: {},
      countries: [],
      loadingImage: require("@/assets/hourglass.gif")
    };
  },
  methods: {
    async fetchCovidData() {
      const res = await fetch("https://api.covid19api.com/summary");
      const data = await res.json();
      return data;
    },
    getCountryData(country) {
      this.status = country;
      this.title = country.Country;
    },
    async ClearCountry() {
      this.loading = true;
      const data = await this.fetchCovidData();
      this.title = 'Global';
      this.status = data.Global;
      this.loading = false;
    }
  },
  async created() {
    const data = await this.fetchCovidData();
    this.dataDate = data.Date;
    this.status = data.Global;
    this.countries = data.Countries;
    this.loading = false;
    console.log(this.countries);

  },

}
</script>
