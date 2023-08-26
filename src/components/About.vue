<template>
    <b-container>
      <b-row class="justify-content-center">
        <b-col sm="3" class="sound-left-sidebar">
          <b-card>
            <b-card-text><i class="fa-solid fa-house" /> Home </b-card-text>
            <b-card-text><i class="fa-solid fa-magnifying-glass" /> Search </b-card-text>
          </b-card>
          
          <b-card>
            <b-card-text><i class="fa-regular fa-bookmark"></i> Library <i class="fa-solid fa-plus"></i></b-card-text>
          </b-card>
          <div class="sound-menu">
            <p>Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.</p>
          </div>
        </b-col>
        <b-col class="sound-right-sidebar">
          <div>
              <div>
                <b-card-group>
                  <b-card  class="sound-card col-6">
                    <b-card-img src="https://picsum.photos/400/400/?image=20" alt="Image" class="rounded-0"></b-card-img>
                    <b-card-text>
                      This card has supporting text below as a natural lead-in to additional content.
                    </b-card-text>
                    <button v-on:click="toggalMusic({'id':'1'})" class="sound-toggal-music">play music</button>
                  </b-card>
                  <b-card class="sound-card col-6">
                    <b-card-img src="https://picsum.photos/400/400/?image=43" alt="Image" class="rounded-0"></b-card-img>
                    <b-card-text>
                      This card has supporting text below as a natural lead-in to additional content.
                    </b-card-text>
                    <button v-on:click="toggalMusic({'id':'2'})"  class="sound-toggal-music">play music</button>
                  </b-card>
                  <b-card class="sound-card col-6">
                    <b-card-img src="https://picsum.photos/400/400/?image=56" alt="Image" class="rounded-0"></b-card-img>
                    <b-card-text>
                      This card has supporting text below as a natural lead-in to additional content.
                    </b-card-text>
                    <button v-on:click="toggalMusic({'id':'3'})" class="sound-toggal-music">play music</button>
                  </b-card>
                  <b-card class="sound-card col-6">
                    <b-card-img src="https://picsum.photos/400/400/?image=56" alt="Image" class="rounded-0"></b-card-img>
                    <b-card-text>
                      This card has supporting text below as a natural lead-in to additional content.
                    </b-card-text>
                    <button v-on:click="toggalMusic({'id':'4'})" class="sound-toggal-music">play music</button>
                  </b-card>
                </b-card-group>
              </div>
            </div>
        </b-col>
      </b-row>
    </b-container>
</template>
<script>
export default {
  name: 'About',
  data () {
    return {
      msg: 'Welcome to Your About Page',
      playing : false,
      music : new Audio()
    }
  },
  methods: { 
      toggalMusic(data) {

          const URL = 'https://s3-us-west-2.amazonaws.com/s.cdpn.io/123941/Yodel_Sound_Effect.mp3';

          const ctx = new AudioContext();
          // let audio;
          const fetchSong = async (path) => {
              const xhr = await fetch(path);
              const arrayBuffer = await xhr.arrayBuffer();
              return ctx.decodeAudioData(arrayBuffer);
          };
          function playback() {
            const songDataPromise = fetchSong(URL);

            songDataPromise.then((audioBuffer) => {
                const playSound = ctx.createBufferSource();
                playSound.buffer = audioBuffer;
                playSound.connect(ctx.destination);
                playSound.start(ctx.currentTime);
            });
          }
          playback();
      }
  }
}

</script>

<style>
.sound-menu {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.sound-left-sidebar{
  background-color: #c4bbbb;
}
.sound-right-sidebar{
  background-color: #93d14c;
}
.row{
    /* overflow: hidden; */
    max-height: 650px;
}
.card{
  margin: 10px;
  border-radius: 10px;
}
.sound-toggal-music{
  display: none;
}
.sound-card:hover .sound-toggal-music {
  display: block;
  background-color: rgba(110, 122, 92, 0.7);
}

.sound-toggal-music {
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  background: rgba(29, 106, 154, 0.72);
  color: #fff;
  visibility: hidden;
  opacity: 0;

  /* transition effect. not necessary */
  transition: opacity .2s, visibility .2s;
}

.sound-card:hover .sound-toggal-music {
  visibility: visible;
  opacity: 1;
}
</style>