<style scoped>
    .container {
        display: flex;
        align-items: center;
        justify-content: center;

        position: absolute;
        z-index: 10;
        left: 5%;
        top: 0;

        width: 20%;
        height: 60px;

        background-color: #fff;
        border-bottom-left-radius: 5px;
        border-bottom-right-radius: 5px;
        border: 2px solid #000;
        border-top: none;

        box-shadow: 1px 2px 15px #444;
    }

    .difficultyChoice {
        border: none;
        width: 30%;
        height: 80%;

        border-radius: 5px;
        margin: 0 1.515%;

        font-size: 20px;
    }

    .difficultyChoice:hover {
        cursor: pointer;
    }

    .difficultyChoice:focus {
        outline: none;
    }

    .selected {
        background-color: #40739e;
        color: #fff;
    }

</style>

<template>
    <div class="container">
        <button class="difficultyChoice" :class="{ selected: mode == 'easy' }" v-on:click="changeMode('easy')">Easy</button>
        <button class="difficultyChoice" :class="{ selected: mode == 'medium' }" v-on:click="changeMode('medium')">Medium</button>
        <button class="difficultyChoice" :class="{ selected: mode == 'hard' }" v-on:click="changeMode('hard')">Hard</button>
    </div>
</template>

<script>
    export default {
        name: 'difficulty',
        methods: {
            changeMode(mode) {
                this.mode = mode;
                this.$emit('mode_change', mode);
            }
        },
        data() {
            return {
                mode: 'easy'
            }
        }
    }
</script>
