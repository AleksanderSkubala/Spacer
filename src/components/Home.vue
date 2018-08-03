<template>
  <div :class="[{marginS: step === 1}, 'wrapper']">
    <div id="content">
        <transition name="slider">
            <img src="../assets/indeks.svg" v-if="step === 1" />
        </transition>
        <transition name="fade" >
            <Hero v-if="step === 0"/>
        </transition>
        <Claim v-if="step === 0" />
        <Search v-model="searchQuery" @input="handler" :dark="step === 1"/>
        <div class="lds-ring" v-if="step === 1 && loading" ></div>
        <transition name="result">
            <div class="results" v-if="wyniki && !loading && step === 1">
                <Results v-for="item in wyniki" :key="item.data[0].nasa_id" :item="item" @click.native="handlerModal(item)"/>
            </div>
        </transition>
    </div>
    <Modal v-if="modalOpen" :photoItem = "photoItem" @closeModal="modalOpen = false"/>
  </div>
</template>

<script>
// import axios from 'axios';
var axios = require('axios');
import debounce from 'lodash.debounce';
import Claim from './Claim.vue';
import Search from './Search.vue';
import Hero from './Hero.vue';
import Results from "./Results.vue";
import Modal from "./Modal.vue";

const API = "https:\\images-api.nasa.gov/search?q=";

export default {
  name: 'home',
  data() {
	return{
        loading: false,
        step: 0,
        searchQuery: "",
		    wyniki: [],
        modalOpen: false,
        photoItem: null,
    };
  },
  methods:{
   handler: debounce(function() {
      this.loading = true;
      console.log(this.searchQuery);
      console.log(`${API}${this.searchQuery}&media_type=image`);
      axios.get(`${API}${this.searchQuery}&media_type=image`)
        .then((response) => {
          this.wyniki = response.data.collection.items;
          this.loading = false;
          this.step = 1;
          console.log(response);
        })
        .catch((error) => {
          console.log(error);
        });
    }, 900),
    handlerModal(i) {
        this.modalOpen = true;
        this.photoItem = i;
    },
    closeModal() {
        this.modalOpen = false;
    },
  },
  components: {
    Claim,
    Search,
    Hero,
    Results,
    Modal,
  }
}
</script>

<style scoped>

.wrapper {
  margin: 0;
  width: 100%;
  height: 100vh;
  padding: 0px;
  margin: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  font-family: "Montserrat", sans-sefir;
  text-align: center;
}
.wrapper.marginS {
  justify-content: flex-start;
  margin-top: 30px;
}
#content {
  display: flex;
  flex-direction: column;
  margin: auto;
}
.results {
  margin-top: 50px;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-gap: 20px;
}
@media only screen and (max-width: 574px) {
  .results {
    grid-template-columns: 1fr;
  }
}
@media (min-width: 575px) and (max-width: 768px) {
  .results {
    grid-template-columns: 1fr 1fr;
  }
}
.fade-enter-active, .fade-leave-active {
  transition: opacity 0.5s ease;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}
.slider-enter-active, .slider-leave-active {
  transition: margin-top 0.5s ease;
}
.slider-enter, .slider-leave-to {
  margin-top: -50px;
}
.result-enter-active, .result-leave-active {
  transition: opacity 0.5s ease;
}
.result-enter, .result-leave-to {
  opacity: 0;
}
.lds-ring {
  display: inline-block;
  position: relative;
  width: 64px;
  height: 64px;
  margin: auto;
  z-index: 100;
}
.lds-ring div {
  box-sizing: border-box;
  display: block;
  position: absolute;
  width: 51px;
  height: 51px;
  margin: 6px;
  border: 6px solid #fff;
  border-radius: 50%;
  animation: lds-ring 1.2s cubic-bezier(0.5, 0, 0.5, 1) infinite;
  border-color: #fff transparent transparent transparent;
}
.lds-ring div:nth-child(1) {
  animation-delay: -0.45s;
}
.lds-ring div:nth-child(2) {
  animation-delay: -0.3s;
}
.lds-ring div:nth-child(3) {
  animation-delay: -0.15s;
}
@keyframes lds-ring {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}



</style>
