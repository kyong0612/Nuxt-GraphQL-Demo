<template>
    <v-expansion-panel>
      <v-expansion-panel-header>{{ referKey }}</v-expansion-panel-header>
      <v-expansion-panel-content class="text-center">
        {{ referValue }}
      </v-expansion-panel-content>
    </v-expansion-panel>
</template>
<script>
export default {
  props: ["referKey", "referValue"]
};
</script>
