<template>
  <div class="row">
    <div class="col-3" v-for="character in characters" :key="character.id">
      <div class="character">
        <img
          :src="character.image"
          :alt="character.name"
          class="img-fluid rounded-circle"
        />
        <p class="text-center">
          {{ character.name }}
          {{ character.origin }}
        </p>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      characters: [],
      API_URL: "https://api.sampleapis.com/rickandmorty/characters",
    };
  },

  mounted() {
    setTimeout(this.callApi, 5000);
  },

  methods: {
    callApi() {
      axios.get(this.API_URL).then((r) => {
        console.log(r.data);
        this.characters = r.data;
        this.loading = false;
      });
    },
  },
};
</script>