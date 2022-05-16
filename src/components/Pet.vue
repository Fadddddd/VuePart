<template>
  <div class="pet">
    <!-- <h3>{{ pet.name }}</h3> -->
    <Card>
      <template #header>
        <img
          src="https://www.primefaces.org/wp-content/uploads/2020/02/primefacesorg-primevue-2020.png"
        />
      </template>
      <template #title> {{ pet.name }} </template>
      <template #subtitle> Age: {{ pet.age }} </template>
      <!-- <template #content>
        <p>
          Lorem ipsum dolor sit amet, consectetur adipisicing elit. Inventore
          sed consequuntur error repudiandae numquam deserunt quisquam repellat
          libero asperiores earum nam nobis, culpa ratione quam perferendis
          esse, cupiditate neque quas!
        </p>
      </template> -->
      <template #footer>
        <Button
          @click="onDelete(pet.id)"
          icon="pi pi-times"
          label="Delete"
          class="p-button-danger"
          style="margin-right: 4em"
        />
        <Button
          icon="pi pi-heart"
          :class="[
            pet.isFavorite ? '' : 'p-button-outlined',
            'p-button-rounded',
            'p-button-danger',
          ]"
        />
      </template>
    </Card>
  </div>
</template>

<script>
export default {
  props: {
    pet: Object,
  },
  components: {},
  methods: {
    onDelete(id) {
      console.log("clicked", id);
    },
  },
};
</script>

<style></style>
