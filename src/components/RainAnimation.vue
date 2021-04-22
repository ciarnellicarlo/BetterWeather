<template>
    <div class="cloud one"></div>
    <div class="cloud two"></div>
    <div class="cloud three"></div>
    <div class="cloud four"></div>
    <div class="cloud five"></div>
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
    </div>
    <div class="rain4">
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
        height: 140px;
        position: absolute;
        left: 0;
        bottom: 0;
        display: flex;
        justify-content: space-between;
        flex-wrap: wrap;
        animation: raining 2.8s infinite linear;
    }

    .rain2 {
        width: 100%;
        height: 130px;
        position: absolute;
        left: -20px;
        bottom: 0;
        display: flex;
        justify-content: space-evenly;
        flex-wrap: wrap;
        animation: raining 1.9s infinite linear;            
    }

    .rain3 {
        width: 100%;
        height: 120px;
        position: absolute;
        left: -10px;
        bottom: 0;
        display: flex;
        justify-content: space-between;
        flex-wrap: wrap;
        animation: raining 1.1s infinite linear;            
    }

    .rain4 {
        width: 100%;
        height: 150px;
        position: absolute;
        left: -30px;
        bottom: 0;
        display: flex;
        justify-content: space-around;
        flex-wrap: wrap;
        animation: raining 1.3s infinite linear;            
    }

    li {
        height: 10px;
        width: 3px;
        background-color: rgba(255, 255, 255, 1);
        list-style-type: none;
        margin: 16px;
        transform: skew(141deg,141deg) translateX(40px);
        filter: drop-shadow(0 0 1px white);
    }

    .cloud {
        position: absolute;
        left: 0;
        background: white;
        border-radius: 1000px;
        opacity: 0.9;
        animation: wind 10s infinite alternate linear;
        filter: drop-shadow(0px 0px 2px white);
    }

    .cloud.one {
        top: 70%;
        width: 65px;
        height: 22px;
    }

    .cloud.two {
        top: 83%;
        width: 48px;
        height: 16px;
        animation-duration: 11s;
    }

    .cloud.three {
        top: 71%;
        width: 55px;
        height: 18px;
        animation-duration: 8s;
    }

    .cloud.four {
        animation-duration: 7s;
        top: 62%;
        width: 46px;
        height: 16px;
    }

    .cloud.five {
        animation-duration: 12s;
        top: 68%;
        width: 70px;
        height: 25px;
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
            opacity: 0.3;
        }
        to {
            transform: translate(-120px, 120px);
            opacity: 0.6;
        }
    }
</style>