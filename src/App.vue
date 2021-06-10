<template>
<body>
   <v-app>
   

    <v-main>
      <Home/>
    </v-main>
  </v-app>
</body>
 
</template>

<script>
import Home from './components/Home';

export default {
  name: 'App',

  components: {
    Home,
  },

  data: () => ({
    //
  }),
};
</script>

<style scoped>
#app{
  background-color:whitesmoke !important;
}
</style>