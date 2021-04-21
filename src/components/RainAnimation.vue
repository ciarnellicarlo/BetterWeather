<template>
    <div class="cloud one"></div>
    <div class="cloud two"></div>
    <div class="cloud three"></div>
    <div class="cloud four"></div>
    <div class="rain1">
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
    </div>
    <div class="rain2">
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
    </div>
    <div class="rain3">
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
    </div>
</template>

<script>
export default {
    name: "RainAnimation"
}
</script>

<style scoped lang="scss">
    .rain1 {
        width: 100%;
        height: 130px;
        position: absolute;
        left: 0;
        bottom: 0;
        display: flex;
        justify-content: space-between;
        flex-wrap: wrap;
        animation: raining 0.4s infinite linear;
    }

    .rain2 {
        width: 100%;
        height: 120px;
        position: absolute;
        left: -20px;
        bottom: 0;
        display: flex;
        justify-content: space-between;
        flex-wrap: wrap;
        animation: raining 0.6s infinite linear;            
    }

    .rain3 {
        width: 100%;
        height: 110px;
        position: absolute;
        left: -10px;
        bottom: 0;
        display: flex;
        justify-content: space-between;
        flex-wrap: wrap;
        animation: raining 0.6s infinite linear;            
    }

    li {
        height: 10px;
        width: 3px;
        background-color: rgba(255, 255, 255, 1);
        list-style-type: none;
        margin: 16px;
        transform: skew(140deg,140deg) translateX(40px);
        filter: drop-shadow(0 0 1px white);
    }

    .cloud {
        position: absolute;
        left: 0;
        background: white;
        border-radius: 1000px;
        opacity: 0.9;
        animation: wind 6s infinite linear;
        filter: drop-shadow(0px 0px 2px white)
    }

    .cloud.one {
        top: 90%;
        width: 60px;
        height: 20px;
    }

    .cloud.two {
        top: 80%;
        width: 45px;
        height: 15px;
        animation-duration: 7s;
    }

    .cloud.three {
        top: 70%;
        width: 50px;
        height: 16px;
        animation-duration: 5s;
    }

    .cloud.four {
        animation: wind 9s infinite linear;
        top: 84%;
        width: 43px;
        height: 15px;
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

    @keyframes raining {
        from {
            transform: translate(0);
            opacity: 0.8;
        }
        to {
            transform: translate(-45px, 45px);
            opacity: 0.4;
        }
    }
</style>