<template>
    <div class="sun"></div>
    <div class="cloud"></div>
</template>

<script>
export default {
    name: "SunAnimation"
}
</script>

<style scoped lang="scss">
    .sun {
        position: absolute;
        background-color: yellow;
        width: 60px;
        height: 60px;
        border-radius: 100%;
        right: 20px;
        bottom: 70px;
        animation: movement 2s infinite alternate ease-in-out;
        filter: drop-shadow(0px 0px 6px rgb(0, 0, 0, 0.4));
    }

    .cloud {
        position: absolute;
        left: 0;
        background: white;
        border-radius: 1000px;
        opacity: 0.9;
        animation: wind 6s infinite linear;
        filter: drop-shadow(0px 0px 1px);
        top: 86%;
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

    @keyframes movement {
        from {
            bottom: 60px;
            opacity: 0.9;
        }
        
        to {
            bottom: 80px;
            transform: scale(1.1);
            opacity: 0.95;
        }
    }

    @keyframes wind {
        from {
            left: 0;
            transform: translateX(-100%)
        }

        to {
            left: 100%;
            transform: translateX(0%)
        }
    }
</style>