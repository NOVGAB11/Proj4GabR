<script setup>
  import {ref, computed} from 'vue'
  import UserInputSong from './components/UserInputSong.vue';
  import Playlist from './components/Playlist.vue';

  const playlist = ref([]);
  const nowPlaying = ref(null);
  

  const addSong = (songDetail) => {
    if (songDetail.artist && songDetail.song){
      playlist.value.push({ artist: songDetail.artist, song: songDetail.song});
    }
  };

  const settingNowPlaying = (song) => {
    nowPlaying.value = song;
  };

  const songCount = computed(() => playlist.value.length);

  const removeSongFromPlaylist = (songBeingRemoved) => {
    playlist.value = playlist.value.filter((song) => song.name !== songBeingRemoved.name);
  };
</script>


<template>
  <main class="app">
    <h1>Playlist Tracker</h1>

    <section class="user-input-song">
      <UserInputSong @addSong="addSong" />
    </section>

    <section class="playlist">
      <Playlist
      :playlist="playlist"
      :onSongClick="settingNowPlaying"
      @removeSong="removeSongFromPlaylist"
      />
    </section>


    <section class="song-playing">
      <h3>Now Playing</h3>
      <p v-if="nowPlaying"> &#9835 Currently Playing &#9835 : {{nowPlaying.song}} by {{nowPlaying.artist}}</p>
      <p v-else>Nothing is playing right now...</p>
    </section>

    <section class="song-count">
      <h3>Total Songs: {{ songCount}}</h3>
    </section>


  </main>
 

</template>
