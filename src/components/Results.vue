<template>
<div :style="style" id="zdj" />
</template>

<script>
export default{
    name: "Results",
    props:{
        item: {
             type: Object,
             required: true,
        },
    },
    data(){
        return{
            photo: this.item.links[0].href,
            title: this.item.data[0].title,
        };
    },
    computed: {
        style() {
            return `background-image: url("${this.photo}")`;
        },
    }
}
</script>

<style scoped>
#zdj{
    width: 300px;
    height: 200px;
    background-size: cover;
    background-repeat: no-repeat;
    background-position: 50%;
}

#zdj:hover{
    cursor: pointer;
}
</style>