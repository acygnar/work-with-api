<template>
  <article class="item">
    <div class="img__wrapper">
      <img :src="mountain.image" alt="" />
    </div>
    <div class="content__wrapper">
      <h1>{{ mountain.title }}</h1>
      <ul>
        <li v-for="country in mountain.countries" :key="country">
          {{ country }}
        </li>
      </ul>
      <p>{{ mountain.description }}</p>
      <nuxt-link :to="`/nauka/${mountain.slug}/`">Więcje</nuxt-link>
    </div>
  </article>
</template>

<script>
export default {
  name: "Mountain",
  props: ["mountain"]
};
</script>

<style scoped lang="sass">
.item
  display: flex
  gap: 127px
.content__wrapper
    h1
        font-size: 48px
        line-height: 57px
    ul
        display: flex
        gap: 5px
    p
        font-size: 18px
        line-height: 30px
        max-width: 628px
</style>
