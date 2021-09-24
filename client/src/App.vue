<template>
  <v-app>
    <LogoBar></LogoBar>
    <v-main>
      <CarCards :cars="carsList" @refresh="getData()"></CarCards>
    </v-main>
  </v-app>
</template>

<script>
import LogoBar from '@/components/LogoBar.vue';
import CarCards from '@/components/CarCards.vue';
import axios from 'axios';
export default {
  name: 'App',
  data: () => ({
    carsList: [],
  }),
  methods: {
    async getData() {
      try {
        const { data } = await axios({
          url: `http://127.0.0.1:3000/cars`,
          method: 'GET',
        });
        this.carsList = data;
      } catch (error) {
        console.error(error);
      }
    },
  },
  created() {
    this.getData();
  },
  components: {
    LogoBar,
    CarCards,
  },
};
</script>
