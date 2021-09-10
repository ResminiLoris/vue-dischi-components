<template>
  <div class="header">
        <div class="container">
          <img src="../assets/img/logo.png" />
          <select v-model="selectedGenre">
            <option>All</option>
            <option v-for="(genre,index) in genreList" :key="index">{{genre}}</option>
          </select>
        </div>
  </div>
</template>

<script>
export default {
    name:'Header',
    data(){
        return{
            selectedGenre: 'all',
        }
    },
    props:['genreList'],
}
</script>
    
<style>
.header {
    background-color: #2e3a46;
    height: 70px;
    padding: 10px;
}

.header img {
    height: 50px;
}

.header .container{
    height: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
}
</style>