<template>
  <div class="grid">
    <div class="col-12 md:col-6 lg:col-3" v-for="pet in pets" :key="pet.id">
      <!-- <h3>{{ pet.name }}</h3> -->
      <Pet :pet="pet" />
    </div>
  </div>
</template>

<script>
import Pet from "./Pet";
export default {
  props: {
    pets: Array,
  },
  components: { Pet },
};
</script>

<style></style>
