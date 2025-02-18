<script setup>
import { defineProps, defineEmits } from 'vue';

const props =defineProps({
  playlist: Array,
  onSongClick: Function
});

const emit = defineEmits();

const removeSong = (songBeingRemoved) => {
  emit('removeSong', songBeingRemoved);
};


</script>

<template>
  <main class="playlist">
    <h2>Playlist</h2>
    <ul>
      <li v-for="(song, index) in props.playlist" :key="index">
        <span @click="props.onSongClick(song)">
          {{song.song}} by {{song.artist}}
        </span>
       <button @click.stop="removeSong(song)">Remove Song</button>
      </li>
    </ul>  
  </main>
 

</template>
