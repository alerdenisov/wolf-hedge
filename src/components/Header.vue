<template>
  <div class="parallax-root absolute top-0 w-full h-full">
    <sky-component
      class="fixed inset-0 parallax parallax--fixed"
    ></sky-component>
    <div class="moon fixed top-0 z-6"></div>
    <div class="parallax-group">
      <montains2-component v-bind="layerStyles[0]"></montains2-component>
      <montains1-component v-bind="layerStyles[1]"></montains1-component>
      <land-component v-bind="layerStyles[2]"></land-component>
      <forest7-component v-bind="layerStyles[3]"></forest7-component>
      <forest6-component v-bind="layerStyles[4]"></forest6-component>
      <forest5-component v-bind="layerStyles[5]"></forest5-component>
      <forest4-component v-bind="layerStyles[6]"></forest4-component>
      <forest3-component v-bind="layerStyles[7]"></forest3-component>
      <forest2-component v-bind="layerStyles[8]"></forest2-component>
      <forest1-component v-bind="layerStyles[9]"></forest1-component>
      <tree2-component v-bind="layerStyles[10]"></tree2-component>
      <tree1-component v-bind="layerStyles[11]"></tree1-component>
      <wolf-component v-bind="layerStyles[12]"></wolf-component>
    </div>
    <div class="night-shadow fixed top-0"></div>
    <div v-if="false" class="configurator fixed z-50 left-0 top-0 bg-white">
      <div class="layer" v-for="(place, index) in layers" :key="index">
        <input type="range" v-model="place.layer" min="0" max="50" />
      </div>
      <pre>{{ configuration }}</pre>
    </div>
  </div>
</template>

<script>
import SkyComponent from "./layers/Sky";
import Montains2Component from "./layers/Montains2";
import Montains1Component from "./layers/Montains1";
import LandComponent from "./layers/Land";
import Forest7Component from "./layers/Forest7";
import Forest6Component from "./layers/Forest6";
import Forest5Component from "./layers/Forest5";
import Forest4Component from "./layers/Forest4";
import Forest3Component from "./layers/Forest3";
import Forest2Component from "./layers/Forest2";
import Forest1Component from "./layers/Forest1";
import Tree2Component from "./layers/Tree2";
import Tree1Component from "./layers/Tree1";
import WolfComponent from "./layers/Wolf";

function place(layer, offset) {
  return { layer, offset };
}
export default {
  components: {
    WolfComponent,
    Tree1Component,
    Tree2Component,
    Forest1Component,
    Forest2Component,
    Forest3Component,
    Forest4Component,
    Forest5Component,
    Forest6Component,
    Forest7Component,
    LandComponent,
    Montains1Component,
    Montains2Component,
    SkyComponent
  },
  data() {
    return {
      layers: [
        place(1, 10),
        place(1, 10),
        place(4, 10),
        place(6, 10),
        place(9, 10),
        place(11, 10),
        place(16, 10),
        place(18, 10),
        place(23, 10),
        place(28, 10),
        place(35, 10),
        place(45, 10),
        place(45, 10)
      ],
      range: [0, 1.1],
      height: 1600
    };
  },
  computed: {
    layerStyles() {
      return this.layers.map(place => ({
        style: {
          transform: this.level(place.layer, place.offset)
        }
      }));
    },
    configuration() {
      return this.layers
        .map(place => `place(${place.layer}, ${place.offset})`)
        .join(",\n");
    }
  },
  mounted() {
    window.addEventListener("scroll", this.onScroll);
    this.onScroll();
  },
  destroyed() {
    window.removeEventListener("scroll", this.onScroll);
  },
  methods: {
    onScroll() {
      const scroll = Math.max(pageYOffset, window.scrollY);
      const height = Math.max(document.documentElement.clientHeight || 0, window.innerHeight || 0)
      const elapsed = scroll / height;
      const [from, to] = this.range;
      const time = Math.min(1, from + elapsed / to);
      this.$el.scrollTo(0, time * this.height);
    },
    scale(n) {
      n = n <= 0 ? 1 / -n : n;
      return (1 / n) * 10;
    },
    level(n, o) {
      const LEVEL_SIZE = 1;
      const PERSPECTIVE = 60;
      const OFFSET_PER_LEVEL = 20;
      let distance = n * LEVEL_SIZE;
      let scale = 1 + (distance * -1) / PERSPECTIVE;
      let offset = o * OFFSET_PER_LEVEL;
      return `translateX(-50%) scale(${scale}) translateZ(${distance}px) translateY(${offset}px)`;
    }
  }
};
</script>

<style type="text/css">
body {
  perspective: 60px;
  perspective-origin: 50% 74vh;
}
.night-shadow {
  width: 1280px;
  height: 1200px;
  box-shadow: inset 0 0 300px 50px #1b1230, inset 0 0 100px 50px #1b1230,
    inset 0 0 15px 30px #1b1230;
  left: 50%;
  top: -200px;
  transform: translate3d(-50%, 0, 0);
}
.moon {
  width: 165px;
  height: 165px;
  border-radius: 110px;
  background-color: white;

  box-shadow: 0 0 250px 3px white;

  left: 50%;
  top: 330px;
  transform: translate3d(-50%, -50%, 0);
}

.parallax-root {
  overflow: hidden;
}

.parallax-group {
  position: relative;
  transform-style: preserve-3d;
}

.parallax {
  width: 1280px;
  left: 50%;
}

.parallax--fixed {
  transform: translateX(-50%);
}

.st0 {
  fill: url(#SVGID_1_);
}
.st1 {
  opacity: 0.1;
  fill: #ffffff;
}
.st2 {
  opacity: 0.2;
  fill: #ffffff;
}
.st3 {
  fill: url(#SVGID_2_);
}
.st4 {
  fill: #ffffff;
}
.st5 {
  fill: #3f2058;
}
.st6 {
  fill: #cf4f5b;
}
.st7 {
  fill: #662a5a;
}
.st8 {
  fill: #8e355b;
}
.st9 {
  fill: #c2495f;
}
.st10 {
  fill: url(#SVGID_3_);
}
.st11 {
  fill: url(#SVGID_4_);
}
.st12 {
  clip-path: url(#SVGID_6_);
}
.st13 {
  fill: #80325b;
}
.st14 {
  fill: #8f375c;
}
.st15 {
  fill: url(#SVGID_7_);
}
.st16 {
  fill: url(#SVGID_8_);
}
.st17 {
  fill: #ae3f5d;
}
.st18 {
  fill: url(#SVGID_9_);
}
.st19 {
  fill: url(#SVGID_10_);
}
.st20 {
  clip-path: url(#SVGID_12_);
}
.st21 {
  fill: url(#SVGID_13_);
}
.st22 {
  fill: url(#SVGID_14_);
}
.st23 {
  fill: url(#SVGID_15_);
}
.st24 {
  fill: url(#SVGID_16_);
}
.st25 {
  fill: url(#SVGID_17_);
}
.st26 {
  fill: url(#SVGID_18_);
}
.st27 {
  fill: url(#SVGID_19_);
}
.st28 {
  fill: url(#SVGID_20_);
}
.st29 {
  fill: url(#SVGID_21_);
}
.st30 {
  fill: url(#SVGID_22_);
}
.st31 {
  fill: url(#SVGID_23_);
}
.st32 {
  fill: url(#SVGID_24_);
}
.st33 {
  fill: url(#SVGID_25_);
}
.st34 {
  fill: url(#SVGID_26_);
}
.st35 {
  fill: url(#SVGID_27_);
}
.st36 {
  fill: url(#SVGID_28_);
}
.st37 {
  fill: url(#SVGID_29_);
}
.st38 {
  fill: url(#SVGID_30_);
}
.st39 {
  fill: url(#SVGID_31_);
}
.st40 {
  fill: url(#SVGID_32_);
}
.st41 {
  fill: #84325a;
}
.st42 {
  clip-path: url(#SVGID_34_);
}
.st43 {
  fill: #692b59;
}
.st44 {
  fill: #687c70;
}
.st45 {
  fill: #64295a;
}
.st46 {
  clip-path: url(#SVGID_36_);
}
.st47 {
  fill: #562557;
}
.st48 {
  fill: #4f2159;
}
.st49 {
  clip-path: url(#SVGID_38_);
}
.st50 {
  fill: #422059;
}
.st51 {
  fill: #35195c;
}
.st52 {
  fill: #251740;
}
.st53 {
  fill: #211739;
}
.st54 {
  clip-path: url(#SVGID_40_);
}
.st55 {
  fill: #1b1230;
}
</style>
