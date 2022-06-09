<template>

  <div>
    <div>

      <v-icon class="icon-perfil">mdi-account</v-icon>
      <span class="user-name">{{ user }}</span>
    </div>

    <div>
      
      <!-- Movernos de una pestaña a otra -->

      <v-tabs class="perfil-tabs">
        <v-tab class="perfil-tab">Favoritos</v-tab>
        <v-tab class="perfil-tab">Escuchar más tarde</v-tab>
        <v-tab class="perfil-tab">Playlist</v-tab>
      </v-tabs>

      <v-container class="grey lighten-5">
        <v-row no-gutters>
          <v-col
            v-for="(item, index) in canciones"
            :key="index"
            cols="12"
            sm="6"
          >
            <RadioComponent
              :name="item.title"
              :subName="item.artist"
              :albun="item.src"
            ></RadioComponent>
            <!-- <v-card class="pa-2" outlined tile>
              {{item.title}}
            </v-card> -->
          </v-col>
        </v-row>
      </v-container>

    </div>
  </div>
</template>

<script>
import { musicArray } from "~/static/musicjson";
import RadioComponent from "~/components/radioComponent.vue";
export default {
  data() {
    return {
      user: {},
      canciones: [],
    };
  },
  mounted() {
    this.user = localStorage.getItem("user")
      ? localStorage.getItem("user")
      : { name: "No hay usuario" };
    this.canciones = musicArray;
  },
  components: { RadioComponent },
};
</script>


<style lang="scss">
.icon-perfil {
  font-size: 220px !important;
}

.user-name {
  font-size: 24px;
  font-weight: bold;
}

.items {
  border: 1px solid white;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

.theme--light.v-tabs > .v-tabs-bar .v-tab:not(.v-tab--active),
.v-tab.v-tab,
.v-tabs-slider {
  color: green;
  caret-color: green ;
}

.perfil-tabs{
  display: flex;
  justify-content: center;
  align-items: center;
}

</style>