<script setup>
  import {ref} from 'vue'
  import UserInputSong from './components/UserInputSong.vue';

  const playlist = ref([]);
  const song = ref('');

  const addSong = (song) => {
    playlist.value.push(song);
  };

  const addSongToPlaylist = () => {
    if (song.value.trim() !== '') {
      emit('addSong', song.value);
      song.value = '';
    }
  };

</script>

<template>
  <main class="app">
    <h1>Playlist Tracker</h1>

    <section class="user-input-song">
      <UserInputSong @addSong="addSong" />

      
    </section>

    <section class="playlist">


    </section>


    <section class="song-playing" v-if="currentSong">


    </section>

    <section class="playlist-duration" v-if="playlist-length > 0">

    </section>


    


  </main>
 

</template>
