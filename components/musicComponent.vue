<template>

<!-- Hoja de la musica traida con json -->

  <div class="music-content">
    <v-card :color="color" dark>
      
      <div class="d-flex flex-no-wrap justify-space-between">

        <div>

          <template>
            <v-card-subtitle
              class="subtitle-music"
              v-text="artist"
            ></v-card-subtitle>
          </template>

          <template v-if="title.length > 12">
            <MARQUEE
              BEHAVIOR="ALTERNATE"
              SCROLLDELAY="400"
              class="music-moviminto"
            >
              <v-card-title class="title-music" v-text="title"></v-card-title>
            </MARQUEE>
          </template>

          <template v-if="title.length <= 12">
            <v-card-title class="title-music" v-text="title"></v-card-title>
          </template>

          <v-card-actions>
            <v-btn
              @click="playpause"
              v-if="type === 'Music'"
              class="ml-2 mt-3"
              fab
              icon
              height="40px"
              right
            >
              <v-icon v-show="play">mdi-play</v-icon>
              <v-icon v-show="!play">mdi-pause</v-icon>
            </v-btn>

            <v-btn v-else class="ml-2 mt-5" outlined rounded small>
              START RADIO
            </v-btn>
          </v-card-actions>
        </div>

        <v-avatar class="ma-3" size="125" tile>
          <v-img :src="src"></v-img>
        </v-avatar>

      </div>

    </v-card>

  </div>
</template>

<style>
.music-content {
  width: 500px;
  height: 20%;
  max-height: 20%;
  margin: 0 0.3%;
}

.title-music {
  width: 128%;
  margin-bottom: -8%;
}

/* .music-moviminto {
    //margin-bottom: -26%;
} */


.color-w {
  color: white !important;
}
.subtitle-music {
  width: 150px;
  height: 10px;
  overflow: hidden;
}
</style>



<script>
import { Howl, Howler } from "howler";
export default {
  name: "musicComponentVue",
  props: {
    title: String,
    artist: String,
    src: String,
    color: String,
    type: String,
  },
  data() {
    return {
      sound: "",
      play: true
    };
  },


  mounted() {
    this.sound = new Howl({
      src: ["/audios/test.mp3"],
    });
  },
  
  methods: {
    playpause() {
      this.play = !this.play;
      this.sound.playing() ? this.sound.pause() : this.sound.play();
    },
  },
};
</script>
