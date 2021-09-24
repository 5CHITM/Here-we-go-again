<template>
  <div>
    <div class="d-flex flex-wrap mb-6 justify-center" color="grey lighten-2" flat tile>
      <div v-for="car in cars" :key="car.id" outlined tile class="ma-3">
        <carCard :car="car"></carCard>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import CarCard from '@/components/CarCard.vue';
export default {
  name: 'CarCards',

  data: () => ({
    cars: [],
  }),
  created() {
    this.getData();
  },
  methods: {
    async getData() {
      try {
        const { data } = await axios({
          url: `http://127.0.0.1:3000/cars`,
          method: 'GET',
        });
        this.cars = data;
      } catch (error) {
        console.error(error);
      }
    },

    async buyCar(el) {
      try {
        await axios({
          url: `http://127.0.0.1:3000/cars/${el.id}`,
          method: 'patch',
          contentType: 'application/json',
          data: {
            title: `${el.title} RESERVED`,
          },
        });
      } catch (error) {
        console.error(error);
      }
    },
  },
  components: {
    CarCard,
  },
};
</script>
