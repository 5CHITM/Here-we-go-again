<template>
  <v-card :loading="loading" class="mx-auto" width="350">
    <template slot="progress">
      <v-progress-linear color="deep-purple" height="10" indeterminate></v-progress-linear>
    </template>

    <v-img width="350" :src="car.image"></v-img>

    <v-card-title>{{ car.title }}</v-card-title>
    <div class="mx-2">
      <p>
        Owner: <strong>{{ car.owner.firstName }} {{ car.owner.lastName }}</strong>
      </p>
      <span>
        Year: <strong>{{ car.yearOfMake }}</strong>
      </span>
      <br />
      <span>
        Miles: <strong>{{ car.miles }}</strong>
      </span>
      <br />
      <br />
      <p>
        Price: <strong>{{ car.price }}</strong>
      </p>
      <p>{{ car.description }}</p>
    </div>

    <v-card-actions>
      <v-btn color="white" class="red" text @click="$emit('buycar', car)">
        Buy car
      </v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
  name: 'CarCard',

  props: {
    car: Object,
  },

  created() {},
};
</script>
