<script setup lang="ts">

</script>

<template>

  <div class="circle">
  </div>
  <div class="circle circle2">
  </div>

</template>

<style scoped>

.circle {
    position: absolute;
    /*border: 1px solid black;*/
    background-color: rgb(131,58,180);
    width: 200px;
    height: 200px;
    border-radius: 50%;
    z-index: 11;
}

.circle2 {
    width: 5px;
    height: 5px;
}

@media (min-width: 1024px) {
}
</style>