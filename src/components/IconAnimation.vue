<template>
    <div class="cloud one"></div>
    <div class="cloud two"></div>
    <div class="cloud three"></div>
</template>

<script>
export default {
    name: "IconAnimation"
}
</script>

<style scoped lang="scss">
    .cloud {
        position: absolute;
        left: 0;
        background: white;
        border-radius: 1000px;
        opacity: 0.8;
    }

    .cloud.one {
        top: 90%;
        left: -20px;
        width: 60px;
        height: 20px;
    }

    .cloud::before {
        content: '';
        position: absolute;
        top: -80%;
        left: 10%;
        width: 50%;
        height: 150%;
        background: white;
        border-radius: 50%;
    }

    .cloud::after {
        content: '';
        position: absolute;
        top: -40%;
        right: 20%;
        width: 30%;
        height: 100%;
        background: white;
        border-radius: 50%;
    }
</style>