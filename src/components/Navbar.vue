<template>
  <nav class="flex bg-white items-center justify-between flex-wrap shadow-md p-6">
    <div class="flex items-center flex-shrink-0 text-white mr-6">
      <span class="font-semibold text-xl tracking-tight">
        <img src="@/assets/logo.svg" alt="API MOVIE">
      </span>
    </div>
    <!-- input form -->
    <form class="relative navbar-form" @submit.prevent="getResults">
      <svg class="absolute navbar-form-search" xmlns="http://www.w3.org/2000/svg" width="18.81" height="18.814" viewBox="0 0 18.81 18.814"><path id="search-solid" d="M18.555,16.266,14.891,12.6a.881.881,0,0,0-.625-.257h-.6a7.639,7.639,0,1,0-1.323,1.323v.6a.881.881,0,0,0,.257.625l3.663,3.663a.878.878,0,0,0,1.246,0l1.04-1.04A.886.886,0,0,0,18.555,16.266ZM7.642,12.345a4.7,4.7,0,1,1,4.7-4.7A4.7,4.7,0,0,1,7.642,12.345Z" fill="#818994"/></svg>
      <input :value="searchTerm" @input="updateValue($event.target.value)"
      class="transition focus:outline-0 border border-transparent
      focus:bg-white placeholder-gray-00 rounded-lg
      bg-gray-200 py-2 pr-4 pl-10 block w-full
      appearance-none leading-normal"
      type="text" placeholder="Search">
    </form>
    <div class="block flex-grow">
      <a href="https://github.com/AssemblyWeb/vue-api" target="_blank"
        class="float-right hover:text-white navbar-github ">
        <svg height="45" aria-hidden="true" focusable="false" data-prefix="fab" data-icon="github" class="svg-inline--fa fa-github fa-w-16" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 496 512"><path class="transition" fill="#3AB982" d="M165.9 397.4c0 2-2.3 3.6-5.2 3.6-3.3.3-5.6-1.3-5.6-3.6 0-2 2.3-3.6 5.2-3.6 3-.3 5.6 1.3 5.6 3.6zm-31.1-4.5c-.7 2 1.3 4.3 4.3 4.9 2.6 1 5.6 0 6.2-2s-1.3-4.3-4.3-5.2c-2.6-.7-5.5.3-6.2 2.3zm44.2-1.7c-2.9.7-4.9 2.6-4.6 4.9.3 2 2.9 3.3 5.9 2.6 2.9-.7 4.9-2.6 4.6-4.6-.3-1.9-3-3.2-5.9-2.9zM244.8 8C106.1 8 0 113.3 0 252c0 110.9 69.8 205.8 169.5 239.2 12.8 2.3 17.3-5.6 17.3-12.1 0-6.2-.3-40.4-.3-61.4 0 0-70 15-84.7-29.8 0 0-11.4-29.1-27.8-36.6 0 0-22.9-15.7 1.6-15.4 0 0 24.9 2 38.6 25.8 21.9 38.6 58.6 27.5 72.9 20.9 2.3-16 8.8-27.1 16-33.7-55.9-6.2-112.3-14.3-112.3-110.5 0-27.5 7.6-41.3 23.6-58.9-2.6-6.5-11.1-33.3 2.6-67.9 20.9-6.5 69 27 69 27 20-5.6 41.5-8.5 62.8-8.5s42.8 2.9 62.8 8.5c0 0 48.1-33.6 69-27 13.7 34.7 5.2 61.4 2.6 67.9 16 17.7 25.8 31.5 25.8 58.9 0 96.5-58.9 104.2-114.8 110.5 9.2 7.9 17 22.9 17 46.4 0 33.7-.3 75.4-.3 83.6 0 6.5 4.6 14.4 17.3 12.1C428.2 457.8 496 362.9 496 252 496 113.3 383.5 8 244.8 8zM97.2 352.9c-1.3 1-1 3.3.7 5.2 1.6 1.6 3.9 2.3 5.2 1 1.3-1 1-3.3-.7-5.2-1.6-1.6-3.9-2.3-5.2-1zm-10.8-8.1c-.7 1.3.3 2.9 2.3 3.9 1.6 1 3.6.7 4.3-.7.7-1.3-.3-2.9-2.3-3.9-2-.6-3.6-.3-4.3.7zm32.4 35.6c-1.6 1.3-1 4.3 1.3 6.2 2.3 2.3 5.2 2.6 6.5 1 1.3-1.3.7-4.3-1.3-6.2-2.2-2.3-5.2-2.6-6.5-1zm-11.4-14.7c-1.6 1-1.6 3.6 0 5.9 1.6 2.3 4.3 3.3 5.6 2.3 1.6-1.3 1.6-3.9 0-6.2-1.4-2.3-4-3.3-5.6-2z"></path></svg>
      </a>
    </div>
  </nav>
</template>

<script>
export default {
  props: ['searchTerm', 'getResults'],
  methods: {
    updateValue(searchTerm) {
      this.$emit('input', searchTerm);
    },
  },
};
</script>
