<template>
  <v-app>
    <LogoBar></LogoBar>
    <v-main>
      <CarCards></CarCards>
    </v-main>
  </v-app>
</template>

<script>
import LogoBar from '@/components/LogoBar.vue';
import CarCards from '@/components/CarCards.vue';
export default {
  name: 'App',
  data: () => ({}),
  components: {
    LogoBar,
    CarCards,
  },
};
</script>
