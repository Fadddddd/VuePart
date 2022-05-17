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
    // addPet(pet) {
    //   this.pets = [...this.pets, pet]; //give all the pets and then add the new one
    // },
    async addPet(pet) {
      const res = await fetch(
        "https://628372e292a6a5e462240cc5.mockapi.io/pets",
        {
          method: "POST",
          headers: {
            "Content-type": "application/json",
          },
          body: JSON.stringify(pet),
        }
      );
      const data = await res.json();
      this.pets = [...this.pets, data];
    },
    // deletePet(id) {
    //   // console.log("Home", id);
    //   if (confirm("Are you sure?")) {
    //     this.pets = this.pets.filter((pet) => pet.id !== id);
    //   }
    // },
    async deletePet(id) {
      if (confirm("Are you sure?")) {
        const res = await fetch(
          `https://628372e292a6a5e462240cc5.mockapi.io/pets/${id}`,
          {
            method: "DELETE",
          }
        );
        res.status == 200
          ? (this.pets = this.pets.filter((pet) => pet.id !== id))
          : alert("Deleting has failed!");
      }
    },
    addFavorite(id) {
      console.log("Home Favorite", id);
      this.pets = this.pets.map((pet) =>
        pet.id === id ? { ...pet, isFavorite: !pet.isFavorite } : pet
      );
    },
    async fetchPets() {
      const res = await fetch(
        "https://628372e292a6a5e462240cc5.mockapi.io/pets"
      );
      const data = await res.json();
      return data;
    },
    async fetchPet(id) {
      const res = await fetch(
        `https://628372e292a6a5e462240cc5.mockapi.io/pets/${id}`
      );
      const data = await res.json();
      return data;
    },
  },
  data() {
    return {
      pets: [],
    };
  },
  async created() {
    this.pets = await this.fetchPets();
    // this.pets = [
    //   {
    //     id: 1,
    //     name: "Katcoot",
    //     age: 6,
    //     url: "https://cdn.pixabay.com/photo/2020/09/01/02/19/cat-5534007__340.jpg",
    //     isFavorite: false,
    //   },
    //   {
    //     id: 2,
    //     name: "Boots",
    //     age: 3,
    //     url: "https://cdn.pixabay.com/photo/2017/09/25/08/04/cat-2784291__340.jpg",
    //     isFavorite: true,
    //   },
    //   {
    //     id: 3,
    //     name: "Grumpy",
    //     age: 3,
    //     url: "https://cdn.pixabay.com/photo/2016/05/07/21/07/cat-1378203__340.jpg",
    //     isFavorite: true,
    //   },
    // ];
  },
};
</script>
