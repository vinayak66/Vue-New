<template>
<the-haeder title="Remember Me"></the-haeder>
<the-resource></the-resource>
 
</template>

<script>

import TheHaeder from './components/layouts/TheHaeder.vue';
import TheResource from './components/learning-resources/TheResource.vue';

export default {
  components: {
    
    TheHaeder,
    TheResource
 
  },
 
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {
  box-sizing: border-box;
}

html {
  font-family: 'Roboto', sans-serif;
}

body {
  margin: 0;
}
</style>