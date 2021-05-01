<template>
  <v-container fluid>
    <v-row dense>
      <v-col v-for="pokemon in pokemons" :key="pokemon.id" :cols="12">
        <v-card>
          <NuxtLink :to="`pokemon/${pokemon.id}`">
            <v-img
              :src="pokemon.image"
              class="white--text align-end"
              gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)"
              contain=true
              height="800"
            >
              <v-card-title v-text="pokemon.name"></v-card-title>
            </v-img>
          </NuxtLink>

          <!-- <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn icon>
              <v-icon>mdi-heart</v-icon>
            </v-btn>

            <v-btn icon>
              <v-icon>mdi-bookmark</v-icon>
            </v-btn>

            <v-btn icon>
              <v-icon>mdi-share-variant</v-icon>
            </v-btn>
          </v-card-actions> -->
        </v-card>
      </v-col>
    </v-row>
    <br>
    <v-expansion-panels accordion>
      <v-expansion-panel>
        <v-expansion-panel-header>Show Query Result</v-expansion-panel-header>
        <v-expansion-panel-content>
          {{ pokemons }}
        </v-expansion-panel-content>
      </v-expansion-panel>
    </v-expansion-panels>
  </v-container>
</template>
<script>
import "vue-apollo";
import pokemons from "~/apollo/queries/pokemons.gql";

// pokemonは最大151匹
let numGetPokemons = 151;

export default {
  data() {
    return {
      pokemons
    };
  },
  // pokemon一覧を取得
  apollo: {
    pokemons: {
      prefetch: "loading",
      query: pokemons,
      variables: {
        amount: numGetPokemons
      }
    }
  },
};
</script>
