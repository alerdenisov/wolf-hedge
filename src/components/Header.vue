<template>
  <div class="parallax-root absolute top-0 w-full h-full">
    <!-- <sky-component
      class="fixed inset-0 parallax parallax--fixed"
      data-key="underStyles"
    ></sky-component> -->
    <div class="moon top-0 parallax__layer z-2" data-key="moonStyles"></div>
    <!-- <div class="parallax-group"> -->
    <!-- <montains2-component
      class="parallax__layer"
      data-key="underStyles"
    ></montains2-component> -->
    <logo-component
      class="logo parallax__layer"
      data-key="logoStyles"
    ></logo-component>
    <logo-component
      class="logo logo--reversed parallax__layer"
      data-key="logoReversedStyles"
    ></logo-component>
    <!-- <montains1-component
      class="parallax__layer"
      data-key="underStyles"
    ></montains1-component> -->
    <land-component class="parallax__layer" data-key="underStyles"></land-component>
    <!-- <forest7-component
      class="parallax__layer"
      data-key="underStyles"
    ></forest7-component>
    <forest6-component
      class="parallax__layer"
      data-key="underStyles"
    ></forest6-component>
    <forest5-component
      class="parallax__layer"
      data-key="underStyles"
    ></forest5-component>
    <forest4-component
      class="parallax__layer"
      data-key="underStyles"
    ></forest4-component>
    <forest3-component
      class="parallax__layer"
      data-key="underStyles"
    ></forest3-component>
    <forest2-component
      class="parallax__layer"
      data-key="underStyles"
    ></forest2-component>
    <forest1-component
      class="parallax__layer"
      data-key="underStyles"
    ></forest1-component>
    <tree2-component
      class="parallax__layer"
      data-key="overlayStyles"
    ></tree2-component>
    <tree1-component
      class="parallax__layer"
      data-key="overlayStyles"
    ></tree1-component> -->
    <wolf-component
      class="parallax__layer"
      data-key="wolfStyles"
    ></wolf-component>
    <!-- </div> -->
    <div class="night-shadow fixed top-0" data-key="faderStyles"></div>
    <!-- <div class="configurator fixed z-50 left-0 top-0 bg-white">
      <pre>{{progress}}</pre>
      <div class="layer" v-for="(place, index) in layers" :key="index">
        <input type="range" v-model="place.layer" min="0" max="50" />
      </div>
      <input type="range" v-model="size" min="0" max="50" />
      <input type="range" v-model="perspective" min="0" max="50" />
      <pre>{{ configuration }}</pre>
    </div> -->
  </div>
</template>

<script>
import LandComponent from "./layers/Land";
// import SkyComponent from "./layers/Sky";
// import Montains2Component from "./layers/Montains2";
// import Montains1Component from "./layers/Montains1";
// import Forest7Component from "./layers/Forest7";
// import Forest6Component from "./layers/Forest6";
// import Forest5Component from "./layers/Forest5";
// import Forest4Component from "./layers/Forest4";
// import Forest3Component from "./layers/Forest3";
// import Forest2Component from "./layers/Forest2";
// import Forest1Component from "./layers/Forest1";
// import Tree2Component from "./layers/Tree2";
// import Tree1Component from "./layers/Tree1";
import WolfComponent from "./layers/Wolf";
import LogoComponent from "./layers/Logo";

function place(layer, offset, index) {
  return { layer, offset, index };
}
export default {
  components: {
    WolfComponent,
    LogoComponent,
    LandComponent,
    // Tree1Component,
    // Tree2Component,
    // Forest1Component,
    // Forest2Component,
    // Forest3Component,
    // Forest4Component,
    // Forest5Component,
    // Forest6Component,
    // Forest7Component,
    // Montains1Component,
    // Montains2Component,
    // SkyComponent
  },
  data() {
    return {
      layers: [
        place(1, 10, 1), // 0
        place(1, 10, 1), // 1
        place(4, 10, 1), // 2
        place(6, 10, 1), // 3
        place(9, 10, 3), // 4
        place(11, 10, 3), // 5
        place(16, 10, 3), // 6
        place(18, 10, 3), // 7
        place(23, 10, 3), // 8
        place(28, 10, 3), // 9
        place(35, 10, 3), // 10
        place(45, 10, 3), // 11
        place(45, 10, 3), // 12
        place(48, 10, 2) // 13
      ],
      range: [0, 1],
      height: 1500,
      progress: 0,
      perspective: 50,
      size: 20,

      els: {
        underStyles: [],
        moonStyles: [],
        logoStyles: [],
        logoReversedStyles: [],
        wolfStyles: [],
        faderStyles: [],
      }
    };
  },
  computed: {
    configuration() {
      return this.layers
        .map(place => `place(${place.layer}, ${place.offset})`)
        .join(",\n");
    }
  },
  mounted() {
    Object.keys(this.els).forEach(key => {
      this.els[key] = Array.from(this.$el.querySelectorAll(`[data-key=${key}]`))
    })
    window.addEventListener("scroll", this.onScroll)
    this.onScroll();
  },
  destroyed() {
    window.removeEventListener("scroll", this.onScroll)
  },
  methods: {
    onScroll() {
      const scroll = Math.max(pageYOffset, window.scrollY);
      const [from, to] = this.range;
      const elapsed = scroll / this.height;
      const time = Math.min(1, from + elapsed / to);
      this.progress = time;

      Object.keys(this.els).forEach(key => {
        this.els[key].forEach(el => (el.style.cssText = this[key]()));
      });
    },

    underStyles() {
      return `z-index: 0; opacity: ${1 - Math.min(1, this.progress / 0.29)}`
    },
    moonStyles() {
      return `z-index: 1; top: ${(this.progress > 0.29 ? this.height * 0.29 : 0)}px; position: ${this.progress > 0.29 ? "absolute" : "fixed"}`
    },
    logoStyles() {
      return `opacity: ${1 - Math.min(1, this.progress / 0.29)}; top: ${(295 + (this.progress > 0.29 ? this.height * 0.29 : 0))}px; position: ${this.progress > 0.29 ? "absolute" : "fixed"}`
    },
    logoReversedStyles() {
      return `z-index: 2; opacity: ${Math.min(1, this.progress / 0.29)}; top: ${(295 + (this.progress > 0.29 ? this.height * 0.29 : 0))}px; position: ${this.progress > 0.29 ? "absolute" : "fixed"}`
    },
    wolfStyles() {
      return `z-index: 3`
    },
    faderStyles() {
      return `opacity: ${1 - Math.max(0, Math.min(1, (this.progress - 0.5) / 0.5))}`
    },
    scale(n) {
      n = n <= 0 ? 1 / -n : n;
      return (1 / n) * 10;
    },
    level(t, n) {
      t *= 2;
      n *= 0.5;
      const PERSPECTIVE = this.perspective;
      const distance = n * this.size;
      const scale = 1 + ((PERSPECTIVE - distance) * -1) / PERSPECTIVE;
      const shift = this.height * (1 - t) * scale;
      return `translate3d(-50%, ${shift.toFixed(2)}px, 0)`;
      // const LEVEL_SIZE = 1;
      // let scale = 1 + (distance * -1) / PERSPECTIVE;
      // let offset = o * OFFSET_PER_LEVEL;
      // return `translateX(-50%) scale(${scale}) translateZ(${distance}px) translateY(${offset}px)`;
    }
  }
};
</script>

<style type="text/css">
body {
  /* perspective: 60px; */
  /* perspective-origin: 50% 74vh; */
}
.night-shadow {
  width: 1280px;
  height: 1200px;
  box-shadow: inset 0 0 300px 50px #1b1230, inset 0 0 100px 50px #1b1230,
    inset 0 0 15px 30px #1b1230;
  left: 50%;
  top: -200px;
  transform: translate3d(-50%, 0, 0);
  z-index: 4;
}
.moon {
  width: 1280px;
  height: 1500px;
  left: 50%;
}
.moon::after {
  content: " ";
  display: block;
  position: absolute;
  top: 30%;
  left: 50%;
  margin: -80px;
  width: 160px;
  height: 160px;
  border-radius: 110px;
  background-color: white;

  box-shadow: 0 0 250px 3px white;

  left: 50%;
  top: 295px;
}

.logo {
  max-width: 100%;
  top: 295px;
  height: 110px;
  margin-top: -55px;
}

.logo--reversed * {
  fill: white !important;
}

.parallax-root {
  overflow: hidden;
  pointer-events: none;
}

.parallax-group {
  position: relative;
  transform-style: preserve-3d;
}
.parallax__layer {
  z-index: 1;
  position: absolute;
  transform: translateX(-50%);
  display: block;
  /* transition: transform 0.1s linear; */
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
