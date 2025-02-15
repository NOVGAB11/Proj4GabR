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
      <ul>
        <li v-for="(song, index) in playlist" :key="index" @click="settingNowPlaying(song)">
          {{ song }}
        </li>
      </ul>
    </section>


    <section class="song-playing">
      <h2>Now Playing</h2>
      <p v-if="nowPlaying"> &#9835 Currently Playing &#9835 : {{nowPlaying}}</p>
      <p v-else>Nothing is playing right now...</p>
    </section>



    <section class="playlist-duration" v-if="playlist-length > 0">

    </section>


    


  </main>
 

</template>
