<template>
  <section>
    <transition mode="out-in" appear name="test">
      <div
        class="container"
        v-if="tabsSelected === tabId"
        v-html="content"
      ></div>
    </transition>
    <div class="connector" v-if="tabsSelected === tabId">
      Komunikacja z rodzicem

      <button @click="handleClick">Change</button>

      Wartość w dziecku: {{ childParent }}
    </div>
  </section>
</template>
<script>
export default {
  props: ["tabsSelected", "content", "tabId", "parent"],
  data() {
    return {
      childParent: this.parent
    };
  },
  methods: {
    handleClick() {
      console.log("klik");
      this.childParent = !this.childParent;

      this.$emit("change-parent", this.tabId);
    }
  }
};
</script>
<style lang="sass" scoped>
.container
    height: 100px
    position: absolute
    width: 80vw
.test-enter-active,.test-leave-active
  transition: opacity 0.5s

.test-enter, .test-leave-to
  opacity: 0
.connector
    padding-top: 200px
button
    border: 1px solid black
    padding: 5px
    transition: 0.5s
    &:hover
        border: 1px solid red
</style>
