<template>
  <v-app>
    <v-app-bar
      app
      color="white"
    >
      <div class="d-flex align-center">
        <v-img
          alt="Sibulabs"
          class="shrink mt-1 hidden-sm-and-down"
          contain
          min-width="100"
          src="https://i1.wp.com/sibulabs.com/wp-content/uploads/2019/03/logo_letras.png?fit=142%2C22&ssl=1"
          width="100"
        />
      </div>
    </v-app-bar>
    <v-main>
      
      <router-view/>
      <FooterComponent />
    </v-main>

  </v-app>
</template>

<script>
import FooterComponent from './components/FooterComponent';
export default {
  name: 'App',
  components: {
    FooterComponent,
  },
  data: () => ({
    //
  }),
};
</script>
