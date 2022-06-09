
<template>
  <div class="container">
     <div class="music">
      <h3>Recomendado para ti</h3>
      <br/>
      <v-sheet class="mx-auto">
        <v-slide-group multiple show-arrows>
          <v-slide-item v-for="(item,index) in musica" :key="index">
            <musicComponentVue :title="item.title" :artist="item.artist" :src="item.src" :color="item.color"
              :type="item.type"></musicComponentVue>
          </v-slide-item>
        </v-slide-group>
      </v-sheet>
    </div>

    <br/>

    <div class="music">
      <h3>Podcast</h3>
      <br/>
      <v-sheet class="mx-auto">
        <v-slide-group multiple show-arrows>
          <v-slide-item v-for="(item,index) in postcast" :key="index">
            <musicComponentVue :title="item.title" :artist="item.artist" :src="item.src" :color="item.color"
              :type="item.type"></musicComponentVue>
          </v-slide-item>
        </v-slide-group>
      </v-sheet>
    </div>

    <br/>

     <div class="music">
      <h3>Programas</h3>
      <br/>
      <v-sheet class="mx-auto">
        <v-slide-group multiple show-arrows>
          <v-slide-item v-for="(item,index) in programas"   v-slot="{ active, toggle }">
            <cardComponent :stHour="item.stHour" :fnHour="item.fnHour" :cTitle="item.cTitle" :cPresentatorName="item.cPresentatorName" :cPresentatorImg="item.cPresentatorImg"></cardComponent>
          </v-slide-item>
        </v-slide-group>
      </v-sheet>
    </div>
  </div>

</template>

<script>
import musicComponentVue from '~/components/musicComponent.vue';
import { postcast } from '~/static/potcast';
import { musicArray } from '~/static/musicjson';
import { programas } from '~/static/Programas'
import cardComponent from '~/components/cardComponent.vue';

export default {
  name: "principalPage",
  components: { musicComponentVue },
  data() {
    return {
      postcast: [],
      musica: [],
      programas:[]
    }
  },
  methods: {
    desordenar(element) {
      element = element.sort(() => { return Math.random() - 0.5 });
      return element;
    }
  },
   mounted() {
      this.postcast = this.desordenar(postcast)
      this.musica = this.desordenar(musicArray)
      this.programas = this.desordenar(programas)
  }
}

</script>



<style>
.container {
  background-color: white;
}

.v-application .mx-auto {
  max-width: 100%;
}

.flex {
  display: flex;
}
</style>