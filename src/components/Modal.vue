<template>
<div class="wrapper">
    <div :class="[{all: more === true}, 'iWrapper']">
        <div class="photo" v-if="more === false">
            <a :href="href"><img :src="href" /></a>
        </div>
        <div :class="[{allD: more === true}, 'desriptionD']">
            <h2 class="title">{{title}}</h2>
            <p class="description">
                {{description}}
            </p> <br/>
            <div id="more" @click="Zmien" >{{txtMore}}</div>
        </div>
        <div class="close" @click="$emit('closeModal')"/>
    </div>
</div>
</template>

<script>
export default{
    name: "Modal",
    props: {
        photoItem:{
            type: Object,
            required: true,
        }
    },
    data() {
        return {
            href: null,
            title: null,
            description: null,
            txtMore: "More...",
            more: false,
        };
    },
    methods: {
        Zmien() {
            if(this.more){
                this.description = this.photoItem.data[0].description.substr(0, 200)+" ...";
                this.more = false;
                this.txtMore = "More ...";
            }
            else{
                this.description = this.photoItem.data[0].description;
                this.more = true;
                this.txtMore = "Less";

            }
        },
    },
    mounted() {
        this.href = this.photoItem.links[0].href;
        this.title = this.photoItem.data[0].title;
        if(this.photoItem.data[0].description.length >= 200){
            this.description = this.photoItem.data[0].description.substr(0, 200)+"...";
        }
        else{
            this.description = this.photoItem.data[0].description;
            this.txtMore = "";
        }
    },
}
</script>

<style scoped>

.wrapper {
  width: 100%;
  height: 100vh;
  background-color: rgba(0, 0, 0, 0.4);
  z-index: 100;
  position: fixed;
  left: 0;
  top: 0;
}
.iWrapper {
  width: 100%;
  min-height: 300px;
  height: auto;
  background-color: #f6f6f6;
  border: none;
  border-radius: none;
  padding: 20px;
  z-index: 101;
  margin: auto;
  display: flex;
  flex-direction: column;
  position: relative;
  overflow-y: visible;
}
.iWrapper .photo {
  width: 100%;
  max-height: 50vh;
  height: auto;
}
.iWrapper .photo img {
  min-width: 305;
  max-width: 70%;
  max-height: 50vh;
  width: auto;
  height: auto;
}
.iWrapper .desriptionD {
  max-width: 50%;
  height: auto;
  max-height: 50vh;
}

.iWrapper .allD{
  max-width: 100%;
  clear: both;
  height: auto;
}

.all{
  width: 100% !important;
  max-height: 80vh !important;
  height: 60vh !important;
  background-color: #f6f6f6;
  border: none;
  border-radius: none;
  padding: 20px;
  z-index: 101;
  margin: auto;
  display: flex;
  flex-direction: column;
  position: relative;
  overflow-y: visible;
}

@media (min-width: 1024px) {
  .iWrapper {
    width: 90%;
    height: auto;
    background-color: #f6f6f6;
    border: none;
    padding: 20px;
    z-index: 101;
    margin: auto;
    display: flex;
    flex-direction: column;
    position: relative;
    flex-direction: row;
  }
  .iWrapper .photo {
    width: 50%;
    max-height: 50vh;
    height: auto;
    font-family: "Montserrat", sans-sefir;
  }
  .iWrapper .photo img {
    max-height: 50vh;
    width: auto;
  }
  .iWrapper .descriptionD {
    max-width: 50%;
    width: 50%;
    height: auto;
  }
}

#all{
  width: 100% !important;
  clear: both;
}

h2.title {
  font-weight: bold;
  font-size: 25px;
  padding: 5px;
  border-bottom: 2px solid;
  text-align: left;
}
p.description {
  font-size: 15px;
  font-weight: lite;
  text-align: justify;
  max-width: 100%;
}
.close {
  position: absolute;
  top: 30px;
  right: 5px;
  padding: 0;
  width: 50px;
  height: 50px;
}
.close::after, .close::before {
  position: absolute;
  content: '';
  width: 30px;
  height: 2px;
  display: block;
  background: black;
}
.close::before {
  transform: rotate(45deg);
}
.close::after {
  transform: rotate(-45deg);
}
.close:hover {
  cursor: pointer;
}
#more {
  color: blue;
  font-size: 20px;
  font-weight: semi-bold;
}
#more:hover {
  cursor: pointer;
}


</style>