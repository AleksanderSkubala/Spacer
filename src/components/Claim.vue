<template>
    <div id="wrapperClaim">
        <h1 id="claim">SPACER</h1> <br/>
        <p class="pClaim">~by Aleksander Skubała</p>
        <p class="pClaim">Begin your journey through our beautiful and mystery Space.</p>
        <p class="pClaim">1. Type the space-related word.</p>
        <p class="pClaim">1. Be amazed.</p>
    </div>
</template>

<script>
    export default{
        name: "Claim"
    }
</script>

<style scoped>

.wrapperClaim{
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    color: white !important;
    font-family: "Montserrat", sans-sefir;
}

#claim{
    font-size: 40px;
    font-weight: bold;
    color: white;
}

.pClaim{
    font-size: 15p;
    font-weight: semi-bold;
    color: white;
}

</style>