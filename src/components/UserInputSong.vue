<script setup>
import {ref, defineEmits} from 'vue';

const artist = ref('');
const song = ref('');
const emit = defineEmits();

const addSongToPlaylist = () => {
    if (artist.value.trim() !== '' && song.value.trim() !== '') {
      emit('addSong', {artist: artist.value, song:song.value});
      artist.value = '';
      song.value = '';
    }
  };
</script>

<template>
  <div>
    <h3> Let's add a song to the PLaylist!</h3>
    <input type="text" v-model="song" placeholder="Enter song name" />
    <button @click="addSongToPlaylist">&#9835 Add Song &#9835</button>
  </div> 
    
</template>
