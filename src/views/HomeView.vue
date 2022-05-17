<template>
  <!-- <div class="home"></div> -->
  <AddPet />
  <Pets @delete-pet="deletePet" :pets="pets" />
</template>

<script>
import Pets from "../components/Pets";
import AddPet from "../components/AddPet.vue";
export default {
  name: "HomeView",
  components: { Pets, AddPet },
  methods: {
    deletePet(id) {
      // console.log("Home", id);
      if (confirm("Are you sure?")) {
        this.pets = this.pets.filter((pet) => pet.id !== id);
      }
    },
  },
  data() {
    return {
      pets: [
        {
          id: 1,
          name: "Katcoot",
          age: 6,
          img: "../assets/Katcoot.jpeg",
          isFavorite: false,
        },
        {
          id: 2,
          name: "Boots",
          age: 3,
          img: "../assets/Boots.jpeg",
          isFavorite: true,
        },
        {
          id: 3,
          name: "Grumpy",
          age: 3,
          img: "https://th.bing.com/th/id/OIP.yaH5Lssb5jLA_pH3SSx2JAHaEs?w=313&h=199&c=7&r=0&o=5&dpr=1.25&pid=1.7",
          isFavorite: true,
        },
      ],
    };
  },
};
</script>
