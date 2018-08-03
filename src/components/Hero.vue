<template>
    <div id="hero" />
</template>

<script>
export default{
    name: "Hero"
}
</script>

<style scoped>

#hero{
    position: absolute;
    width: 100%;
    height: 100vh;
    top: 0;
    left: 0;
    z-index: -1;
    background-image: url("../assets/heroimage.jpg");
    background-repeat: no-repeat;
    background-size: cover;
    background-position: 80% 0%;
}

#hero::after{
    content: "";
    width: 100%;
    height: 100vh;
    z-index: 0;
    position: absolute;
    top: 0;
    left: 0;
    background-color: rgba(0,0,0, .3);
}

</style>