<template>
<div>
  {{ pokemon }}
</div>
</template>
<script lang="ts">
import Vue from 'vue'
// import gql from 'graphql-tag'
import 'vue-apollo'
import pokemon from '~/apollo/queries/pokemons.gql'


// tsではVueを継承しないとエラーになる
export default Vue.extend({
  data(){
    return{
      pokemon
    }
  },
  apollo: {
    pokemon:{
      query:pokemon
    }
  }
})

</script>

