<template>
  <v-col>
    <v-row align="end">

      <v-col offset-sm="4" sm="4">
        <v-select @change="onChange()" v-model="selected" outlined :items="countries" persistent-hint color="grey"
          item-value="ID" item-text="Country" filled rounded class="mt-10  pa-3" label="Select Country">
        </v-select>
      </v-col>

    </v-row>
  </v-col>
</template>
<script>
export default {
  name: "Country_Select",
  props: ["countries"],
  data() {
    return {
      selected: 0,
    };
  },
  methods: {
    onChange() {
      const country = this.countries.find((item) => item.ID === this.selected);
      console.log(country);
      this.$emit("get-country", country);
    }
  },
};
</script>