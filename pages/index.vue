<script setup lang="ts">
const { find } = useStrapi();
// import type {Player} from '~/models/player.model';

const { data, pending, error } = await useAsyncData("players", async () => {
  return await find("players", {
    populate: "*",
  }).then((res) => res.data);
});

/*  */
</script>

<template>
  <div>
    <h1>Personnes</h1>
    <!--     <pre v-if="data">{{ data }}</pre>
    lien cliquable avec slug
    {{ data }} -->

    <template v-if="pending">
      <p>Loading...</p>
    </template>
    <template v-else>
      <!--       <pre>{{ data }}</pre>
 -->
      <div class="my-4">
        <!-- <div v-for="player in players?.data" :key="player.slug">
                    <a :href="/players/${player.slug}">{{ player.name }}</a>
                </div> -->
        <div v-for="player in data" :key="player.slug">
          <h3 :href="`/players/${player.slug}`">{{ player.name }}</h3>
          <div v-for="competitions in player" :key="competitions.name">
            <p>Gagnant de {{ competitions.name }}</p>
          </div>
        </div>
      </div>
    </template>
  </div>
</template>

<style>
/* font */
@font-face {
  font-family: "wix-madefor-text";
  font-weight: 400;
  src: url("/fonts/WixMadeforText-Regular.woff2") format("woff2");
}

@font-face {
  font-family: "wix-madefor-text";
  font-weight: 500;
  src: url("/fonts/WixMadeforText-Medium.woff2") format("woff2");
}

@font-face {
  font-family: "wix-madefor-text";
  font-weight: 600;
  src: url("/fonts/WixMadeforText-SemiBold.woff2") format("woff2");
}

@font-face {
  font-family: "wix-madefor-text";
  font-weight: 700;
  src: url("/fonts/WixMadeforText-Bold.woff2") format("woff2");
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "wix-madefor-text", sans-serif;
}

a {
  color: #000000;
  text-decoration: none;
  transition: ease-in-out 0.3s;
  &:hover {
    color: #4c4e97;
  }
}
</style>
