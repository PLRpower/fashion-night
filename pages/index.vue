<script setup>
import { ref } from 'vue';

// Références aux éléments du DOM
const audio = ref(null); // Référence à l'élément audio
const play = ref(null); // Référence au bouton play
const pause = ref(null); // Référence au bouton pause

// État de lecture
const isPlaying = ref(false);

// Fonction pour basculer entre lecture et pause
const togglePlay = () => {
  isPlaying.value = !isPlaying.value;
  if (isPlaying.value) {
    audio.value.play();
  } else {
    audio.value.pause();
  }
};

const send = ref(false);
const email = ref('');

// Fonction pour soumettre le formulaire
async function submitForm() {
  await $fetch('https://api.tnptrading.fr/email-fashion-night', {
    method: 'POST',
    body: {
      email: email.value
    }
  });
  send.value = true;
}

// Utilisation de useFetch (si nécessaire)
const { data } = await useFetch('https://api.tnptrading.fr/email-fashion-night');
</script>

<template>
  <h2 class="ms-6 text-4xl lg:text-6xl mt-16 cardinal">Strasbourg 2025</h2>
  <h1 class="text-center text-6xl lg:text-8xl mt-8 cardinal">Fifty <span
      class="text-4xl lg:text-6xl cardinal">and</span> Fabulous,</h1>
  <h1 class="text-end me-6 text-6xl lg:text-8xl mt-8 cardinal">the fashion night</h1>
  <div class="flex justify-center mt-16">
    <div class="bg-black movie">
      <video class="w-full h-full" src="/img/video.webm" autoplay muted loop></video>
    </div>
    <nuxt-img class="z-10 w-11/12 lg:w-2/3" src="/img/ecran.webp"></nuxt-img>
  </div>
  <h2 class="text-center text-5xl mt-32 cardinal">Save the date :</h2>
  <p class="text-center text-4xl mt-4 cardinal">Calendrier officiel, 22 mars 2025</p>
  <h1 class="cardinal text-center text-5xl mt-32 mb-4">Lookbook à venir</h1>
  <p class="cardinal text-4xl text-center mb-32">Restez connectés</p>

  <h2 class="text-center text-5xl mt-32 cardinal">Préreservez dès maintenant :</h2>
  <form @submit.prevent="submitForm" v-show="!send">
    <div class="flex justify-center mt-8 gap-x-4">
      <input class="h-12 w-1/3 text-center text-2xl border-b-2 border-black mb-32 cardinal outline-none" type="email"
             placeholder="votre adresse email" id="email" name="email" v-model="email">
      <button type="submit" class="h-12 w-1/6 bg-black text-white text-2xl mb-32 cardinal">Valider</button>
    </div>
  </form>
  <p class="cardinal text-center text-green-800 text-2xl mb-32 mt-4" v-show="send">Votre préinscription est maintenant confirmée.</p>

  <div
      class="fixed w-36 h-12 bg-black bottom-5 right-5 rounded-full flex items-center px-4 ease-in-out transition hover:scale-105 justify-evenly cursor-pointer"
      @click="togglePlay">
    <img class="w-6 h-6" src="/img/play.svg" alt="Play" ref="play" v-show="!isPlaying">
    <img class="w-6 h-6" src="/img/pause.svg" alt="Pause" ref="pause" v-show="isPlaying">
    <p class="text-white">Ambiance</p>
  </div>

  <audio class="fixed bottom-0 right-0" src="/music.mp3" ref="audio"></audio>


</template>

<style scoped>
@media (max-width: 1024px) {
  .movie {
    width: 89% !important;
  }
}

.movie {
  width: 65%;
  aspect-ratio: 12 / 7;
  position: absolute;
  margin-top: 1%;
  margin-left: auto;
  margin-right: auto;
}
</style>
