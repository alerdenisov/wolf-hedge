<template>
  <div>
    <navbar-component></navbar-component>
    <main class="bg-dark-night">
      <div
        class="relative pt-16 pb-32 flex content-center items-center justify-center"
        style="height: 1300px;"
      >
        <header-component />
        <div class="container relative mx-auto" style="margin-top: -30vh">
          <div class="items-center flex flex-wrap">
            <div class="w-full lg:w-6/12 px-4 ml-auto mr-auto text-center">
              <fader-component class="pt-20" :from="0.72" :to="2">
                <h1 class="text-white font-semibold text-5xl">
                  Hawl with us
                </h1>
                <p class="mt-4 text-lg text-gray-300">
                  Join to wolf flock to protect your legacy from dangerous
                  environment
                </p>
              </fader-component>
            </div>
          </div>
        </div>
      </div>
      <section class="pb-20 relative block bg-gray-900 bg-dark-night">
        <div
          class="bottom-auto top-0 left-0 right-0 w-full absolute pointer-events-none overflow-hidden -mt-20"
          style="height: 80px; transform: translateZ(0px);"
        >
          <svg
            class="absolute bottom-0 overflow-hidden"
            xmlns="http://www.w3.org/2000/svg"
            preserveAspectRatio="none"
            version="1.1"
            viewBox="0 0 2560 100"
            x="0"
            y="0"
          >
            <polygon
              class="bg-dark-night"
              points="2560 0 2560 100 0 100"
            ></polygon>
          </svg>
        </div>
        <div class="container mx-auto px-4 lg:pb-64">
          <div class="flex flex-wrap text-center justify-center">
            <fader-component class="w-full lg:w-6/12 px-4" :from="0.12" :to="2">
              <h2 class="text-4xl font-semibold text-white">Hawl with us</h2>
              <p class="text-lg leading-relaxed mt-4 mb-4 text-gray-500">
                Fully Decentralized Autonomous organization cooperating as per
                the transparent rules coded in Ethereum smart-contracts to
                govern Wolfage Finance Ecosystem by WEFI token holders.
              </p>
            </fader-component>
          </div>
          <div class="flex flex-wrap mt-12 justify-center">
            <div class="w-full lg:w-3/12 px-4 text-center">
              <div
                class="text-gray-900 p-3 w-12 h-12 shadow-lg rounded-full bg-white inline-flex items-center justify-center"
              >
                <i class="fas fa-chart-line text-xl"></i>
              </div>
              <h6 class="text-xl mt-5 font-semibold text-white">
                Unique ecomonic
              </h6>
              <p class="mt-2 mb-4 text-gray-500">
                Unique economic model aimed at attracting additional liquidity
                and value growth.
              </p>
            </div>
            <div class="w-full lg:w-3/12 px-4 text-center">
              <div
                class="text-gray-900 p-3 w-12 h-12 shadow-lg rounded-full bg-white inline-flex items-center justify-center"
              >
                <i class="fas fa-star text-xl"></i>
              </div>
              <h5 class="text-xl mt-5 font-semibold text-white">
                Transparent and secure
              </h5>
              <p class="mt-2 mb-4 text-gray-500">
                Track each transaction of whole ecosystem and that everything is
                being carried out as per the on-chain and off-chain governance
                rules.
              </p>
            </div>
            <div class="w-full lg:w-3/12 px-4 text-center">
              <div
                class="text-gray-900 p-3 w-12 h-12 shadow-lg rounded-full bg-white inline-flex items-center justify-center"
              >
                <i class="fas fa-lightbulb text-xl"></i>
              </div>
              <h5 class="text-xl mt-5 font-semibold text-white">
                Manipulated by flock
              </h5>
              <p class="mt-2 mb-4 text-gray-500">
                Decentralized governance allows the market to be manipulated in
                order to generate more profit.
              </p>
            </div>
          </div>
        </div>
      </section>

      <section class="pb-20 bg-gray-300 -mt-24">
        <div class="container mx-auto px-4">
          <div class="flex flex-wrap">
            <div class="lg:pt-12 pt-6 w-full md:w-4/12 px-4 text-center">
              <div
                class="relative flex flex-col min-w-0 break-words bg-white w-full mb-8 shadow-lg rounded-lg"
              >
                <div class="px-4 py-5 flex-auto">
                  <div
                    class="text-white p-3 text-center inline-flex items-center justify-center w-12 h-12 mb-5 shadow-lg rounded-full bg-red-400"
                  >
                    <i class="fas fa-award"></i>
                  </div>
                  <h6 class="text-xl font-semibold">Awarded Agency</h6>
                  <p class="mt-2 mb-4 text-gray-600">
                    Divide details about your product or agency work into parts.
                    A paragraph describing a feature will be enough.
                  </p>
                </div>
              </div>
            </div>
            <div class="w-full md:w-4/12 px-4 text-center">
              <div
                class="relative flex flex-col min-w-0 break-words bg-white w-full mb-8 shadow-lg rounded-lg"
              >
                <div class="px-4 py-5 flex-auto">
                  <div
                    class="text-white p-3 text-center inline-flex items-center justify-center w-12 h-12 mb-5 shadow-lg rounded-full bg-blue-400"
                  >
                    <i class="fas fa-retweet"></i>
                  </div>
                  <h6 class="text-xl font-semibold">Free Revisions</h6>
                  <p class="mt-2 mb-4 text-gray-600">
                    Keep you user engaged by providing meaningful information.
                    Remember that by this time, the user is curious.
                  </p>
                </div>
              </div>
            </div>
            <div class="pt-6 w-full md:w-4/12 px-4 text-center">
              <div
                class="relative flex flex-col min-w-0 break-words bg-white w-full mb-8 shadow-lg rounded-lg"
              >
                <div class="px-4 py-5 flex-auto">
                  <div
                    class="text-white p-3 text-center inline-flex items-center justify-center w-12 h-12 mb-5 shadow-lg rounded-full bg-green-400"
                  >
                    <i class="fas fa-fingerprint"></i>
                  </div>
                  <h6 class="text-xl font-semibold">Verified Company</h6>
                  <p class="mt-2 mb-4 text-gray-600">
                    Write a few lines about each one. A paragraph describing a
                    feature will be enough. Keep you user engaged!
                  </p>
                </div>
              </div>
            </div>
          </div>
          <div class="flex flex-wrap items-center mt-32">
            <div class="w-full md:w-5/12 px-4 mr-auto ml-auto">
              <div
                class="text-gray-600 p-3 text-center inline-flex items-center justify-center w-16 h-16 mb-6 shadow-lg rounded-full bg-gray-100"
              >
                <i class="fas fa-user-friends text-xl"></i>
              </div>
              <h3 class="text-3xl mb-2 font-semibold leading-normal">
                Growing with us is a pleasure
              </h3>
              <p
                class="text-lg font-light leading-relaxed mt-4 mb-4 text-gray-700"
              >
                Compound is an algorithmic, autonomous interest rate protocol
                built for developers, to unlock a universe of open financial
                applications.
              </p>
              <p
                class="text-lg font-light leading-relaxed mt-0 mb-4 text-gray-700"
              >
                Compound is an algorithmic, autonomous interest rate protocol
                built for developers, to unlock a universe of open financial
                applications.
              </p>
              <a
                href="https://www.creative-tim.com/learning-lab/tailwind-starter-kit#/presentation"
                class="font-bold text-gray-800 mt-8"
                >Start earn</a
              >
            </div>
            <div class="w-full md:w-4/12 px-4 mr-auto ml-auto">
              <div
                class="relative flex flex-col min-w-0 break-words bg-white w-full mb-6 shadow-lg rounded-lg bg-pink-600"
              >
                <img
                  alt="..."
                  src="https://images.unsplash.com/photo-1577980888576-4ba53bae1c69?ixlib=rb-1.2.1&amp;ixid=eyJhcHBfaWQiOjEyMDd9&amp;auto=format&amp;fit=crop&amp;h=850&amp;w=1051&amp;q=80"
                  class="w-full align-middle rounded-t-lg"
                />
                <blockquote class="relative p-8 mb-4">
                  <svg
                    preserveAspectRatio="none"
                    xmlns="http://www.w3.org/2000/svg"
                    viewBox="0 0 583 95"
                    class="absolute left-0 w-full block"
                    style="height: 95px; top: -94px;"
                  >
                    <polygon
                      points="-30,95 583,95 583,65"
                      class="text-pink-600 fill-current"
                    ></polygon>
                  </svg>
                  <h4 class="text-xl font-bold text-white">
                    Breed cubs
                  </h4>
                  <p class="text-md font-light mt-2 text-white">
                    Earn extra value from breeding NFT tokens of unique cubs
                  </p>
                  <p class="text-md font-light mt-5 text-white">
                    <button
                      class="bg-white text-gray-800 hover:bg-transparent active:bg-gray-100 text-xs font-bold uppercase px-4 py-2 rounded shadow hover:shadow-md outline-none focus:outline-none"
                      type="button"
                      style="transition: all 0.15s ease 0s;"
                    >
                      More details
                    </button>
                  </p>
                </blockquote>
              </div>
            </div>
          </div>
        </div>
      </section>
    </main>
    <footer-component></footer-component>
  </div>
</template>
<script>
import NavbarComponent from "../components/Navbar.vue";
import FooterComponent from "../components/Footer.vue";
import HeaderComponent from "../components/Header.vue";
import FaderComponent from "../components/Fader.vue";

export default {
  name: "landing-page",
  components: {
    NavbarComponent,
    FooterComponent,
    FaderComponent,
    HeaderComponent
  }
};
</script>

<style>
.bg-dark-night {
  background-color: #1b1230;
  fill: #1b1230;
}
</style>
