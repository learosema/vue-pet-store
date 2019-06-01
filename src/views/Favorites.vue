<template>
  <div>
    <v-list>
      <v-subheader v-if="!favorites.length">Your favorites list is empty</v-subheader>
      <div v-else>
        <v-list-tile avatar v-for="(dog, index) in favorites" :key="dog.breed" @click="{}">
          <v-list-tile-avatar>
            <img :src="dog.img">
          </v-list-tile-avatar>
          <v-list-tile-content>{{dog.name}}</v-list-tile-content>
          <v-list-tile-action>
            <v-icon @click="removeFromFavorites(dog)">delete</v-icon>
          </v-list-tile-action>
        </v-list-tile>
        <v-btn to="/form">Adopt</v-btn>
      </div>
    </v-list>
  </div>
</template>
<script>
import { mapActions } from "vuex";

export default {
  methods: {
    ...mapActions(["removeFromFavorites"])
  },
  computed: {
    favorites() {
      return this.$store.state.favorites;
    }
  }
};
</script>