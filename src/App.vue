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
</style>

<template>
    <div class="container">
        <colourTab :colour="colour"></colourTab>
        <winScreen v-show:if="pick == true && win == true" :winningColour="colour"></winScreen>
        <loseScreen v-show:if="pick == true && win == false" :winningColour="colour"></loseScreen> 
        <colourSquare v-for="n in 16" @colour="pushColour" @clicked="checkAns"></colourSquare>
    </div>
</template>

<script>
    import colourSquare from './components/colourSquare.vue';
    import colourTab from './components/colourTab.vue';
    import winScreen from './components/winScreen.vue';
    import loseScreen from './components/loseScreen.vue';

    export default {
        name: 'app',
        components: {
            colourSquare,
            colourTab,
            winScreen,
            loseScreen
        },
        // watch: {
        //     // function(this.colours.)
        // },
        methods: {
            pushColour(colour) {
                this.colours.push(colour);
            },
            checkAns(answer) {
                this.pick = true;
                if(answer === this.colour) {
                    this.win = true;
                } else if( answer !== this.colour) {
                    this.win = false;
                }
            }
        },
        mounted() {
            let randomNum = Math.floor(Math.random() * 15);
            this.colour = this.colours[randomNum];
            console.log(randomNum);
        },
        data() {
            return {
                colours: [],
                win: false,
                pick: false,
                colour: ''
            }
        }
    }
</script>
