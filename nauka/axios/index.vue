<template>
  <main>
    <div class="con">
      <h1>AXIOS</h1>
    </div>
    <hr />
    <hr />

    <div class="wrapper">
      <div v-html="pageContent"></div>
    </div>
  </main>
</template>
<script>
import axios from "axios";

export default {
  layout: "subpage",

  async asyncData(context) {
    let slug = context.route.path.replace("/", "");

    const pageContent = await axios(
      `http://localhost/ngk-wp-api/wp-json/wp/v2/pages?slug=${slug}`
    ).then(json => json.data[0].content.rendered);
    const pageACF = await axios(
      `http://localhost/ngk-wp-api/wp-json/wp/v2/pages?slug=${slug}`
    ).then(json => console.log(json.data));
    return { pageContent, pageACF };
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
