<template lang="html">
    <div>
        <div class="card-img-top movie-card"
        v-bind:style='{ backgroundImage: "url(" + movie.Poster + ")", }'
        >
        </div>
        <h5 class="card-title mt-2 font-weight-bold">{{movie.Title}}</h5>
        <p class="card-text">
            {{movie.Year}}
        </p>
        <a :href="'https://www.imdb.com/title/' + movie.imdbID" target="_blank" class="btn btn-danger">See movie</a>
        <a @click="addFav(movie)" class="btn btn-primary mt-2">add</a>
    </div>
</template>

<script>
export default {
  props: ['movie', 'addFav', 'removeFav'],
};
</script>
