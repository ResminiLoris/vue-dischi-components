<template>
    <div class="card">
        <img :src="album.poster" :alt="album.title" />
        <h2 class="title">{{album.title}}</h2>
        <address class="author">{{album.author}}</address>
        <time datetime="1988" class="year">{{album.year}}</time>
    </div>
</template>

<script>
export default {
    name:"Album",
    props:['album'],
}
</script>

<style>
 
.card {
  background-color: #2e3a46;
  padding: 20px;
  margin: 20px;
  flex-basis: 200px;
  text-align: center;
  min-height: 350px;
}

.card img {
  width: 100%;
  height: auto;
}

.card .title {
  color: #fff;
  margin: 15px 0;
}
.card .author,
.card .year {
  color: #808080;
  font-size: 21px;
}
.card .year {
  font-size: 16px;
}

</style>