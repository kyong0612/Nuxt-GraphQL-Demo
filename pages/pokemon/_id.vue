<template>
  <div v-if="pokemon">
    <v-container fluid>
      <v-img
        :src="pokemon.image"
        class="white--text align-end"
        gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)"
        height="800px"
      >
        <v-card-title v-text="pokemon.name"></v-card-title>
      </v-img>
      <v-expansion-panels focusable>
        <!-- classification -->
        <single-explanation
          referKey="Classification"
          :referValue="pokemon.classification"
        />
        <!-- types -->
        <multi-explanation referKey="Types" :referValue="pokemon.types" />
        <!-- resistant -->
        <multi-explanation
          referKey="Resistant"
          :referValue="pokemon.resistant"
        />
        <!-- weaknesses -->
        <multi-explanation
          referKey="Weaknesses"
          :referValue="pokemon.weaknesses"
        />
        <!-- evolutions -->
        <evolution-explanation
          v-if="pokemon.evolutions"
          referKey="Evolutions"
          :referValue="pokemon.evolutions"
        />
        <!-- evolutionRequirements -->
        <multi-explanation
          v-if="pokemon.evolutionRequirements"
          referKey="EvolutionRequirements"
          :referValue="pokemon.evolutionRequirements"
        />

        <!-- レスポンス -->
        <v-expansion-panel>
          <v-expansion-panel-header>Show Query Result</v-expansion-panel-header>
          <v-expansion-panel-content class="justify-center">
            {{ pokemon }}
          </v-expansion-panel-content>
        </v-expansion-panel>
      </v-expansion-panels>
    </v-container>
  </div>
</template>

<script>
import pokemon from "~/apollo/queries/pokemon.gql";
import multiExplanation from "~/components/multiExplanation.vue";
import singleExplanation from "~/components/singleExplanation.vue";
import evolutionExplanation from "~/components/evolutionExplanation.vue";

export default {
  apollo: {
    pokemon: {
      query: pokemon,
      prefetch: ({ route }) => ({ id: route.params.id }),
      variables() {
        return { id: this.$route.params.id };
      }
    }
  },
  components: {
    multiExplanation,
    singleExplanation,
    evolutionExplanation
  }
};
</script>
