<script setup>
import { ref, onMounted } from 'vue';

// Références aux éléments du DOM
const audio = ref(null); // Référence à l'élément audio
const play = ref(null); // Référence au bouton play
const pause = ref(null); // Référence au bouton pause
const video = ref(null); // Référence à l'élément vidéo

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

// Fonction pour vérifier et démarrer la lecture de la vidéo
const playVideoIfNotPlaying = () => {
  if (video.value && video.value.paused) {
    video.value.play();
  }
};

// Lancer la vidéo à la fin du chargement
onMounted(() => {
  playVideoIfNotPlaying();
});
</script>

<template>
  <h2 class="ms-6 text-4xl lg:text-6xl mt-16 cardinal">Strasbourg 2025</h2>
  <h1 class="text-center text-6xl lg:text-8xl mt-8 cardinal">Fifty <span
      class="text-4xl lg:text-6xl cardinal">and</span> Fabulous,</h1>
  <h1 class="text-end me-6 text-6xl lg:text-8xl mt-8 cardinal">the fashion night</h1>
  <div class="flex justify-center mt-16">
    <div class="bg-black movie">
      <video class="w-full h-full" src="/img/video.mp4" ref="video" autoplay muted loop playsinline></video>
    </div>
    <nuxt-img class="z-10 w-11/12 lg:w-2/3" src="/img/ecran.webp"></nuxt-img>
  </div>
  <h2 class="text-center text-5xl mt-32 cardinal mx-2">Save the date :</h2>
  <p class="text-center text-4xl mt-4 cardinal">Calendrier officiel, 22 mars 2025</p>

  <h1 class="cardinal text-center text-5xl mt-32 mb-4 mx-2">Lookbook</h1>
  <div class="grid grid-cols-2 gap-2 sm:grid-cols-4 mx-2">
    <div class="flex flex-col gap-2">
      <nuxt-img class="w-full" src="/img/lookbook/2.jpg" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/3.webp" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/4.jpg" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/5.jpg" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/6.jpg" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/7.jpg" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/8.jpg" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/9.jpg" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/10.jpg" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/11.webp" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/12.webp" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/13.webp" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/14.webp" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/50.jpg" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/1.jpg" loading="lazy"></nuxt-img>
    </div>
    <div class="flex flex-col gap-2">
      <nuxt-img class="w-full" src="/img/lookbook/16.webp" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/17.webp" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/18.webp" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/19.webp" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/20.jpg" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/21.webp" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/22.webp" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/23.jpg" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/24.jpg" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/25.jpg" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/26.jpg" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/27.jpg" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/44.jpg" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/28.jpg" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/29.jpg" loading="lazy"></nuxt-img>
    </div>
    <div class="flex flex-col gap-2">
      <nuxt-img class="w-full" src="/img/lookbook/30.jpg" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/31.jpg" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/32.jpg" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/33.jpg" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/34.jpg" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/35.jpg" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/36.jpg" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/37.jpg" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/38.jpg" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/39.jpg" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/40.jpg" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/41.jpg" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/42.jpg" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/43.jpg" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/45.jpg" loading="lazy"></nuxt-img>
    </div>
    <div class="flex flex-col gap-2">
      <nuxt-img class="w-full" src="/img/lookbook/15.jpg" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/46.jpg" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/47.jpg" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/48.jpg" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/49.jpg" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/51.jpg" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/52.jpg" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/53.jpg" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/54.jpg" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/55.jpg" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/56.jpg" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/57.jpg" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/58.jpg" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/59.jpg" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/60.jpg" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/61.jpg" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/62.jpg" loading="lazy"></nuxt-img>
      <nuxt-img class="w-full" src="/img/lookbook/63.jpg" loading="lazy"></nuxt-img>
    </div>

  </div>

  <h2 class="text-center text-4xl lg:text-5xl mx-2 mt-32 cardinal">Préréservez dès maintenant :</h2>
  <form @submit.prevent="submitForm" v-show="!send">
    <div class="flex justify-center mt-8 gap-x-4 mb-4">
      <input class="h-12 w-64 lg:w-96 text-center text-xl border-b-2 border-gray-400 cardinal outline-none focus:border-black" type="email"
             placeholder="votre adresse email" id="email" name="email" v-model="email">
    </div>
    <p class="text-center mb-4">*Votre email est uniquement <span class="text-nowrap">utilisé pour vous contacter.</span><br>Il n'est pas partagé avec des tiers.</p>
    <div class="flex justify-center gap-x-4 mb-32">
      <button type="submit" class="align-middle self-center justify-center h-12 px-4 bg-black text-white text-xl cardinal">Valider</button>
    </div>
  </form>
  <p class="cardinal text-center text-green-800 text-2xl mb-32 mt-4" v-show="send">Votre préinscription est maintenant confirmée.</p>

  <div
      class="fixed w-36 h-12 bg-black bottom-5 right-5 rounded-full flex items-center px-4 ease-in-out transition hover:scale-105 justify-evenly cursor-pointer z-50"
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
