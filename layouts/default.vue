<template>
<!-- Esta es la barra del header -->
  <v-app dark>
    
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant="miniVariant"
      :clipped="clipped"
      fixed
      app
    >
      <v-list>
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>

      
    </v-navigation-drawer>

    <v-app-bar :clipped-left="clipped" fixed app>
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-btn icon @click.stop="fixed = !fixed"> </v-btn>
      <img class="principal-logo" src="../static/onda-cero.png" alt="Onda Cero">
      <v-spacer />
      <v-btn icon @click.stop="rightDrawer = !rightDrawer">
        <v-icon>mdi-bell</v-icon>
        <v-icon>mdi-account</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main>
      <v-container>
        <Nuxt />
      </v-container>
    </v-main>

  </v-app>
</template>

<script>
export default {
  name: "DefaultLayout",
  data() {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: "mdi-apps",
          title: "Principal",
          to: "/principal",
        },
        {
          icon: "mdi-account",
          title: "Perfil",
          to: "/perfil",
        },
        {
          icon: "mdi-login-variant",
          title: "Cerrar Sesión",
          to: "/login",
        },
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: "OndaSanvi",
    };
  },
};
</script>


<style>
  .principal-logo{
    width: 5%;
  }
</style>