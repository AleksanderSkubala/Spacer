<template>
    <div id="wrapperClaim">
        <h1 id="claim">SPACER</h1> <br/>
        <p class="pClaim">~by Aleksander Skubała</p>
        <p class="pClaim space">(Based on Hello Roman app.)</p>
        <p class="pClaim space">Begin your journey through our beautiful and mystery Space.</p>
        <p class="pClaim"><strong>1.</strong> Type the Space-related word.</p>
        <p class="pClaim">(You don't have to press Enter or any other buttons, </br> but whait o moment to load images.)</p>
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
    font-size: 50px;
    font-weight: bolder;
    color: white;
}

.pClaim{
    font-size: 15p;
    font-weight: normal;
    color: white;
}

strong{
    font-weight: 900;
}

.space{
    padding-bottom: 20px;
}

</style>