<script setup>
  import {ref, computed} from 'vue'
  import UserInputSong from './components/UserInputSong.vue';
  import PLaylist from './components/UserInputSong.vue';

  const playlist = ref([]);
  const nowPlaying = ref(null);
  
  const song = ref('');


  const addSong = (songName) => {
    playlist.value.push({name: songName, isFavorite: false});
  };

  const settingNowPlaying = (song) => {
    nowPlaying.value = song;
  };

  const songCount = computed(() => playlist.value.length);

  const removeSongFromPlaylist = (songBeingRemoved) => {
    playlist.value = playlist.value.filter((song) => song.name !== songToRemove.name);
  }
</script>


<template>
  <main class="app">
    <h1>Playlist Tracker</h1>

    <section class="user-input-song">
      <UserInputSong @addSong="addSong" />
    </section>

    <section class="playlist">
      <h2>Playlist</h2>
      <ul>
        <li v-for="(song, index) in playlist" :key="index" @click="settingNowPlaying(song)">
          {{ song }}
        </li>
      </ul>
    </section>


    <section class="song-playing">
      <h3>Now Playing</h3>
      <p v-if="nowPlaying"> &#9835 Currently Playing &#9835 : {{nowPlaying}}</p>
      <p v-else>Nothing is playing right now...</p>
    </section>

    <section class="song-count">
      <h3>Total Songs: {{ songCount}}</h3>
    </section>


  </main>
 

</template>
