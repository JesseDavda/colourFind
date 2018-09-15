<style>
    .container {
        width: 100%;
        height: 100%;
        display: flex;
        align-items: center;
        justify-content: center;
        flex-direction: row;
        flex-wrap: wrap;
    }

    .clickBlocker {
        width: 100%;
        height: 100%;

        position: absolute;
        z-index: 5;
    }
</style>

<template>
    <div class="container">
        <colourTab :colour="colour"></colourTab>
        <difficulty @mode_change="changeMode"></difficulty>
        <winScreen v-show:if="pick == true && win == true" :winningColour="colour"></winScreen>
        <loseScreen v-show:if="pick == true && win == false" :winningColour="colour"></loseScreen>
        <div class="clickBlocker" v-show:if="pick == true"></div>
        <colourSquare v-for="n in numOfSquares" @colour="pushColour" @clicked="checkAns" :height="height"></colourSquare>
    </div>
</template>

<script>
    import colourSquare from './components/colourSquare.vue';
    import colourTab from './components/colourTab.vue';
    import winScreen from './components/winScreen.vue';
    import loseScreen from './components/loseScreen.vue';
    import difficulty from './components/difficulty.vue';

    export default {
        name: 'app',
        components: {
            colourSquare,
            colourTab,
            winScreen,
            loseScreen,
            difficulty
        },
        methods: {
            changeMode(value) {
                console.log(value);
                this.mode = value;
                if(this.mode == 'easy') {
                    this.height = '100%';
                    this.arraySize = 2;
                    this.numOfSquares = 3;
                } else if(this.mode == 'medium') {
                    this.height = '50%';
                    this.arraySize = 5;
                    this.numOfSquares = 6;
                } else if(this.mode == 'hard') {
                    this.height = '33.333%';
                    this.arraySize = 8;
                    this.numOfSquares = 9;
                }
            },
            pushColour(colour) {
                this.colours.push(colour);
            },
            checkAns(answer) {
                this.pick = true;
                if(answer === this.colour) {
                    this.win = true;
                    setTimeout(() => {
                        document.location.reload();
                    }, 3000);
                } else if( answer !== this.colour) {
                    this.win = false;
                    setTimeout(() => {
                        document.location.reload();
                    }, 3000);
                }
            }
        },
        mounted() {
            let randomNum = Math.floor(Math.random() * this.arraySize);
            this.colour = this.colours[randomNum];
            console.log(randomNum);
        },
        data() {
            return {
                mode: 'easy',
                height: '100%',
                arraySize: 2,
                numOfSquares: 3,
                colours: [],
                win: false,
                pick: false,
                colour: ''
            }
        }
    }
</script>
