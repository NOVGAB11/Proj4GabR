<script setup>
import {ref, defineEmits} from 'vue';

const song = ref('');
const emit = defineEmits();

const addSongToPlaylist = () => {
    if (song.value.trim() !== '') {
      emit('addSong', song.value);
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
