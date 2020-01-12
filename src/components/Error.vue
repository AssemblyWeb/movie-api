<template>
    <div v-if="error" class=" text-center py-4 lg:px-4">
        <div class="p-2 bg-red-600 items-center text-indigo-100 leading-none lg:rounded-full flex lg:inline-flex" role="alert">
            <span class="flex rounded-full bg-red-700 uppercase px-2 py-1 text-xs font-bold mr-3">Oops!</span>
            <span class="font-semibold mr-2 text-left flex-auto">{{error}}</span>
        </div>
    </div>
</template>

<script>
export default {
  props: ['error'],
};
</script>
