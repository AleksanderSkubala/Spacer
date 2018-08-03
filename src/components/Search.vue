<template>
<div id="wrapperSearch">
    <div class="search">
        <input name="search" placeholder="e.g. Tytan" :value="value" @input="handlerC" :class="{dark}"/>
    </div>
</div>
</template>

<script>
export default {
  name: 'Search',
  data() {
	return{};
  },
  props: {
    dark: {
        type: Boolean,
        default: false,
    },
    value: {
        type: String,
        required: true,
    },
  },
  methods:{
	handlerC(e){
        this.$emit('input', e.target.value);
    }
  }
}
</script>

<style scoped>
.search {
  min-width: 200px;
  display: flex;
  flex-direction: column;
  align-items: center;
  min-height: 30px;
  color: white;
}
.search input {
  border: none;
  border-bottom: 1.5px solid;
  text-align: center;
  padding: 10px;
  margin-top: 10px;
  font-family: "Montserrat", sans-sefir !important;
  font-weight: light;
  background: none;
  color: white;
  transition: box-shadow 0.6s;
}
.search input:focus {
  outline: none;
  box-shadow: 0px 9px 12px -11px white;
}
.dark {
  color: #1e3d4a !important;
  border-color: #1e3d4a !important;
  justify-content: flex-start;
}
.dark:focus {
  outline: none !important;
  box-shadow: 0px 12px 12px -11px rgba(0, 0, 0, 0.8) !important;
}

</style>
