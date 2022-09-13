
<template>
  <v-app>
    <Header></Header>
    <HomeView></HomeView>

  </v-app>

</template>




<script>
import Header from '@/components/Header.vue';
import HomeView from './views/HomeView.vue';

export default {
  components: {
    Header,
    HomeView
},
};

</script>
