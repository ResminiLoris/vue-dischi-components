<template>
    <div class="main">
        <main class="container">
            <div id="album-container">
                <Album :album="album" v-for="(album,index) in albums" :key="index"/>
            </div>
      </main>
    </div>
</template>

<script>
import Album from './Album.vue'

export default {
    name: 'Main',
    components: {
    Album,
  },
  props:['albums'],
}
</script>

<style>

#album-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
</style>