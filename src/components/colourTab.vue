<style scoped>
    .colourTab {
        display: flex;
        align-items: center;
        justify-content: center;

        position: absolute;
        z-index: 10;
        right: 10%;

        width: 20%;
        height: 60px;

        background-color: #fff;
        border-bottom-left-radius: 5px;
        border-bottom-right-radius: 5px;
        border: 2px solid #000;
        border-top: none;

        box-shadow: 1px 2px 15px #000;
    }

    h4 {
    /* font-size: px; */
        font-weight: 700;
        color: #000;
    }
</style>

<template>
    <div class="colourTab">
        <h4>COLOUR: {{colour.toUpperCase()}}</h4>
    </div>
</template>

<script>
    export default {
        name: 'colourTab',
        props: {
            colour: String
        }
    }
</script>
