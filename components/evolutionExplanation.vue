<template>
  <v-expansion-panel>
    <v-expansion-panel-header>{{referKey}}</v-expansion-panel-header>
    <v-expansion-panel-content v-for="(value, key) in referValue" :key="key" class="text-center">
      <NuxtLink :to="`${value.id}`">
      {{value.name}}
      </NuxtLink>
    </v-expansion-panel-content>
  </v-expansion-panel>
</template>
<script>
export default {
  props:[
    'referKey',
    'referValue'
    ]
};
</script>
