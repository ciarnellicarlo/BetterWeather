<template>
    <div>
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
    div {
        width: 100%;
        height: 160px;
        position: absolute;
        left: 0;
        bottom: 0;
        display: flex;
        justify-content: space-between;
        flex-wrap: wrap;
    }

    li {
        height: 10px;
        width: 3px;
        background-color: rgba(255, 255, 255, 1);
        list-style-type: none;
        margin: 16px;
        transform: skew(140deg,140deg);
    }
</style>