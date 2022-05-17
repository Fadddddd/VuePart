<template>
  <div class="grid">
    <div class="col-12 md:col-6 lg:col-3" v-for="pet in pets" :key="pet.id">
      <!-- <h3>{{ pet.name }}</h3> -->
      <Pet
        @delete-pet="$emit('delete-pet', pet.id)"
        @add-favorite="$emit('add-favorite', pet.id)"
        :pet="pet"
      />
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
  emits: ["delete-pet", "add-favorite"],
};
</script>

<style></style>
