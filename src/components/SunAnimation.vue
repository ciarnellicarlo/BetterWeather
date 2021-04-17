<template>
    <div class="sun"></div>
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
    }

    @keyframes movement {
        from {
            bottom: 60px;
            opacity: 0.8;
        }
        
        to {
            bottom: 80px;
            transform: scale(1.1);
            opacity: 0.9;
        }
    }
</style>