<template>
  <span class="replacer">
    <transition
      name="animate__animated"
      enter-active-class="animate__animated animate__fadeInDown animate__faster"
      leave-active-class="animate__animated animate__fadeOutDown animate__faster"
      mode="out-in"
    >
      <div class="rep rep-first" v-if="first" key="first">{{ first }}</div>
      <div class="rep rep-second" v-else key="second">{{ second }}</div>
    </transition>
  </span>
</template>

<script>
export default {
  name: "Replacer",
  props: ["content"],
  data() {
    return {
      first: this.content,
      second: "",
    };
  },
  watch: {
    content(val) {
      if (this.first){
        this.second = val;
        this.first = "";
      }else{
        this.first = val;
        this.second = "";
      }
    },
  },
};
</script>

<style lang="scss">
:root {
  --animate-duration: 500ms;
  --animate-delay: 0;
}

.replacer {
  position: initial;

  .rep {
    position: relative;
    display: inline-block;
    top: 0;
    left: 0;
  }
}
</style>
