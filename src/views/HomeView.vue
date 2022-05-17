<template>
  <!-- <div class="home"></div> -->
  <AddPet @add-pet="addPet" />
  <Pets @delete-pet="deletePet" @add-favorite="addFavorite" :pets="pets" />
</template>

<script>
import Pets from "../components/Pets";
import AddPet from "../components/AddPet.vue";
export default {
  name: "HomeView",
  components: { Pets, AddPet },
  methods: {
    addPet(pet) {
      this.pets = [...this.pets, pet]; //give all the pets and then add the new one
    },
    deletePet(id) {
      // console.log("Home", id);
      if (confirm("Are you sure?")) {
        this.pets = this.pets.filter((pet) => pet.id !== id);
      }
    },
    addFavorite(id) {
      console.log("Home Favorite", id);
      this.pets = this.pets.map((pet) =>
        pet.id === id ? { ...pet, isFavorite: !pet.isFavorite } : pet
      );
    },
  },
  data() {
    return {
      pets: [],
    };
  },
  created() {
    this.pets = [
      {
        id: 1,
        name: "Katcoot",
        age: 6,
        url: "https://cdn.pixabay.com/photo/2020/09/01/02/19/cat-5534007__340.jpg",
        isFavorite: false,
      },
      {
        id: 2,
        name: "Boots",
        age: 3,
        url: "https://cdn.pixabay.com/photo/2017/09/25/08/04/cat-2784291__340.jpg",
        isFavorite: true,
      },
      {
        id: 3,
        name: "Grumpy",
        age: 3,
        url: "https://cdn.pixabay.com/photo/2016/05/07/21/07/cat-1378203__340.jpg",
        isFavorite: true,
      },
    ];
  },
};
</script>
