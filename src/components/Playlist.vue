<script setup>
import { defineProps} from 'vue';

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
      <li v-for="(song, index) in props.playlist" :key="index" @click="props.onSongClick(song)">
        <span @click="props.onSongClick(song)">
          {{song}}
        </span>
       <button @click.stop="removeSong(song)">Remove Song</button>
      </li>
    </ul>  
  </main>
 

</template>
