<template>
    <b-container>
      <b-row>
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
                  <b-card sm="2"  class="sound-card">
                    <b-card-img src="https://picsum.photos/400/400/?image=20" alt="Image" class="rounded-0"></b-card-img>
                    <b-card-text>
                      This card has supporting text below as a natural lead-in to additional content.
                    </b-card-text>
                    <button v-on:click="toggalMusic({'id':'1'})" class="sound-toggal-music">play music</button>
                  </b-card>
                  <b-card sm="2" class="sound-card">
                    <b-card-img src="https://picsum.photos/400/400/?image=43" alt="Image" class="rounded-0"></b-card-img>
                    <b-card-text>
                      This card has supporting text below as a natural lead-in to additional content.
                    </b-card-text>
                    <button v-on:click="toggalMusic({'id':'2'})"  class="sound-toggal-music">play music</button>
                  </b-card>
                  <b-card sm="2" class="sound-card">
                    <b-card-img src="https://picsum.photos/400/400/?image=56" alt="Image" class="rounded-0"></b-card-img>
                    <b-card-text>
                      This card has supporting text below as a natural lead-in to additional content.
                    </b-card-text>
                    <button v-on:click="toggalMusic({'id':'3'})" class="sound-toggal-music">play music</button>
                  </b-card>
                  <b-card sm="2" class="sound-card">
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
        let musicSrc = require(`@/assets/tone/${data.id}.mp3`);
        if(!this.music.src.includes(musicSrc)){
          console.log(this.music.src,'music.Src');
          console.log(musicSrc,'musicSrc');
            // let musicSrc = require(`@/assets/tone/${data.id}.mp3`);
            this.music.src = musicSrc
            this.music.play();
        } else if (!this.music.paused){
          console.log(this.music.src,'src');
          this.music.pause();
          // this.music.currentTime = 0;
        } else if (this.music.src) {
            this.music.play();
          console.log(this.music.currentTime);
          console.log(this.music.duration);
        }

        // if(!this.music.paused){
        //   this.music.pause();
        //   // this.music.currentTime = 0;
        // }else{
        //     let musicSrc = require(`@/assets/tone/${data.id}.mp3`);
        //     this.music.src = musicSrc
        //     this.music.play();

        // }
          // this.music.play();

          
          // if(this.playing == true){
          //   this.music.pause();
          //   // this.playing != this.playing;
          //   // console.log(this.playing);
          // }else{
          //   let musicSrc = require(`@/assets/tone/${data.id}.mp3`);
          //   this.music.src = musicSrc
          //   this.music.play();
          //   // console.log(this.playing);
          // }
          // console.log(this.music.duration,'duration');
          // // console.log(this.music.duration,'duration');
          // this.playing = !this.playing;
          // music.addEventListener("loadeddata", () => {
          //   let duration = music.duration;
          //   console.log(duration);
          // });
          // music.addEventListener("canplaythrough", () => {
          //   let duration = music.load();
          //   console.log(duration,'canplaythrough');
          // });
          // music.addEventListener("timeupdate", () => {
          //   let duration = music.seeking
          //   console.log(duration,'timeupdate');
          // });
          // music.addEventListener("ended", () => {
          //   let duration = music.ended;
          //   console.log(duration,'ended');
          // });
          // music.addEventListener("waiting", () => {
          //   let duration = music.audioWaiting();
          //   console.log(duration,'waiting');
          // });
          // music.addEventListener("playing", () => {
          //   let duration = music.loaded();
          //   console.log(duration,'loaded');
          // });
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
    overflow: hidden;
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
}
</style>


<!-- <button onclick="playAudio()" type="button">Play Audio</button>
<button onclick="pauseAudio()" type="button">Pause Audio</button> 

<script>
let x = new Audio('horse.mp3');
//var x = document.getElementById("myAudio"); 

function playAudio() { 
  x.play(); 
} 

function pauseAudio() { 
  x.pause(); 
} 
</script> -->