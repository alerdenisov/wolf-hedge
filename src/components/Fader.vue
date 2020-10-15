<template>
  <div :class="classes">
    <slot />
  </div>
</template>

<script>
export default {
  props: {
    from: {
      type: Number,
      default: 0.1
    },
    to: {
      type: Number,
      default: 0.9
    }
  },
  data() {
    return {
      enabled: false
    }
  },
  computed: {
    classes() {
      return {
        active: this.enabled,
        root: true
      }
    }
  },
  mounted() {
    window.addEventListener("scroll", this.onScroll);
    this.onScroll()
  },
  destroyed() {
    // eslint-disable-next-line no-console
    console.log("destroy");
    window.removeEventListener("scroll", this.onScroll);
  },
  methods: {
    getCoords() {
      // crossbrowser version
      const box = this.$el.getBoundingClientRect();
      const body = document.body;
      const docEl = document.documentElement;
      const scrollTop = window.pageYOffset || docEl.scrollTop || body.scrollTop;
      const clientTop = docEl.clientTop || body.clientTop || 0;
      const top = box.top + scrollTop - clientTop;

      const height = Math.max(
        document.documentElement.clientHeight || 0,
        window.innerHeight || 0
      );

      const center = box.top + box.height * 0.5;

      const time = 1 - center / height;

      return { offset: top, scroll: scrollTop, top: box.top, time };
    },
    onScroll() {
      const { offset, scroll, top, time } = this.getCoords();
      // const offset = this.$el.getBoundingClientRect();
      // const scroll = Math.max(pageYOffset, window.scrollY);
      // const elapsed = scroll / height;
      // const [from, to] = this.range;
      // const time = Math.min(1, from + elapsed / to);

      // eslint-disable-next-line no-console
      console.log(offset, scroll, top, time);
      this.enabled = time > this.from && time < this.to
    }
  }
};
</script>

<style scoped>
.root {
  transition: opacity 0.2s ease;
  opacity: 0;
}
.active {
  opacity: 1;
}
</style>