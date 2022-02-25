<template>
  <section class="post__wrapper">
    <div class="post__header">
      <h1>{{ mountain.title }}</h1>
    </div>
    <div class="post__body">
      <div class="post__image">
        <img :src="mountain.image" alt="" />
      </div>
      <div class="post__description">
        <div class="post__data">
          <span><strong>Continent: </strong>{{ mountain.continent }}</span>
          <span><strong>Height: </strong>{{ mountain.height }}</span>
          <p class="countries"><strong>Countries: </strong>
          <ul>
            <li v-for="country in mountain.countries" :key="country">
              {{ country }}
            </li>
          </ul>
          </p>
      
        </div>
        <p class="post__txt">
            {{ mountain.description }}
        </p>
      </div>
    </div>
    <nuxt-link to="/nauka/">Wróć</nuxt-link>
  </section>
</template>

<script>
export default {
  name: "slug",
  layout: "subpage",
  async asyncData(data) {
    let slug = data.params.slug;
    const mountain = await fetch(
      `https://api.nuxtjs.dev/mountains/${slug}`
    ).then(res => res.json());

    return { mountain };
  }
};
</script>

<style scoped lang="sass">
.post__wrapper
  position: relative
  z-index: 1
  min-height: 500px
  padding-left: 320px
  padding-right: 60px
  padding-bottom: 20px
  .post__header
      padding-top: 200px
      display: flex
      justify-content: space-between
      h1
          font-size: 48px
          line-height: 57px
          padding-bottom: 70px
  .post__body
       display: flex
       gap: 50px
       padding-bottom: 30px
  .post__description
      h1
          font-size: 48px
          line-height: 57px
      .post__data
          font-size: 18px
          line-height: 30px
          display: flex
          flex-direction: column
.countries
    display: inline-flex
    ul
        display: inline-flex
    li
        margin-right: 5px
        margin-left: 5px
.post__txt
    font-size: 18px
    line-height: 30px
    padding-top: 30px
    max-width: 626px
.nuxt-link-active
    font-size: 22px
    line-height: 30px    
</style>
