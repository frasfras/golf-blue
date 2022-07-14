<template>
<v-container>
    <v-row class="text-center">
      <v-col cols="12">
  <HelloWorld msg="Water plan"/>
  </v-col cols="12">
  </v-row class="text-center">
  </v-container>
      
</template>

<script>
  import HelloWorld from '@/components/CoursesWorld.vue';
/* eslint-disable */
  export default {
    name: 'Home',

    components: {
      HelloWorld,
    },
  }
</script>
