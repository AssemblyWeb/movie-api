<template>
        <div @click="addFav(movie)"
          class="bg-transparent w-1 hover:bg-red-500 text-red-700 font-semibold hover:text-white
          py-2 px-4 border border-red-500 hover:border-transparent rounded ml-2">
          <img src="@/assets/heart.svg"/>
        </div>
</template>

<script>
export default {};
</script>
