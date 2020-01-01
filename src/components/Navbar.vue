<template>
  <nav class="flex items-center justify-between flex-wrap shadow-md p-6">
    <div class="flex items-center flex-shrink-0 text-white mr-6">
      <span class="font-semibold text-xl tracking-tight">
        <img src="@/assets/logo.svg" alt="">
      </span>
    </div>
    <div class="" @submit.prevent="getResults">
      <input v-model="searchTerm" class="transition focus:outline-0 border border-transparent focus:bg-white
    focus:border-gray-300 placeholder-gray-600 rounded-lg bg-gray-200 py-2 pr-4 pl-10 block w-full
    appearance-none leading-normal ds-input" type="text" placeholder="Search">
    </div>
    <div class="block flex-grow">
      <div class="">
        <a href="https://github.com/AssemblyWeb/vue-api" target="_blank"
          class="float-right hover:text-white">
          <img class="w-10" src="@/assets/github-brands.svg"
            alt="https://github.com/AssemblyWeb/vue-api">
        </a>
      </div>
    </div>
  </nav>
</template>
