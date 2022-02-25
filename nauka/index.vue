<template>
  <main>
    <div class="con">
      <h1>Nauka</h1>
    </div>
    <hr />
    <!-- <div v-html="mountains"></div> -->
    <hr />

    <div class="wrapper" v-for="mountain in mountains" :key="mountain.title">
      <Mountain :mountain="mountain" />
    </div>
  </main>
</template>
<script>
import Mountain from "@/components/nauka/Mountain.vue";
export default {
  layout: "job",
  components: { Mountain },
  async asyncData() {
    const mountains = await fetch(
      "https://api.nuxtjs.dev/mountains"
    ).then(res => res.json());

    return { mountains };
  }
};
</script>
<style lang="sass">
main
  position: relative
  z-index: 1
.wrapper
  padding: 60px
</style>
