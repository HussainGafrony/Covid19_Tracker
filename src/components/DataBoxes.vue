<template>
  <v-row class=" justify-center">
    <div class="d-flex justify-center ma-4">
        <v-card width="350" color="#BBDEFB">
            <v-card-title class=" justify-center font-weight-bold font pa-2 blue darken-3--text">Cases</v-card-title>
            <v-card-title class=" justify-center font-weight-bold font pa-1">New: {{numberWithCommas( status.NewConfirmed) }}
            </v-card-title>
            <v-card-title class=" justify-center font-weight-bold font pa-0 mb-4">
                Total: {{ numberWithCommas(status.TotalConfirmed) }}
            </v-card-title>
        </v-card>
    </div>
    <div class="d-flex justify-center ma-4">
        <v-card width="350" color="#BBDEFB">
            <v-card-title class=" justify-center font-weight-bold font pa-2 blue darken-3--text">Deaths</v-card-title>
            <v-card-title class=" justify-center font-weight-bold font pa-1">New: {{ numberWithCommas(status.NewDeaths) }}
            </v-card-title>
            <v-card-title class=" justify-center font-weight-bold font pa-0 mb-4">
                Total: {{ numberWithCommas(status.TotalDeaths) }}
            </v-card-title>
        </v-card>
    </div>
</v-row>
</template>
<script>
export default {
    name: 'DataBoxes',
    props: ['status'],
    methods:{
        numberWithCommas(x) {
    return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
}
    }
}

</script>