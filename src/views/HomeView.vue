<template>
  <div class="home"></div>
  <Pets :pets="pets" />
</template>

<script>
import Pets from "../components/Pets";
export default {
  name: "HomeView",
  components: { Pets },
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
