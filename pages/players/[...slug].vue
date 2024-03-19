<script setup lang="ts">
const { findOne } = useStrapi();
const route = useRoute();
const { data, pending } = useAsyncData("player", () =>
  findOne(`players/${route.params.slug}`).then((res) => res.data)
);
</script>

<template>
  <!--   <div>{{ data }}</div>
 -->
  <div v-if="pending">
    <p>Loading...</p>
  </div>
  <div v-else>
    <h1>{{ data }}</h1>
  </div>
</template>
