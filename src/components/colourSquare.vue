<style scoped>
    div {
        box-sizing: border-box;
        -moz-box-sizing: border-box;
        -webkit-box-sizing: border-box;

        width: 33.333%;
        height: 100%;
        box-shadow: inset 0 0 3px #444;
    }

    div:hover {
        cursor: pointer;
        opacity: 0.7;
    }
</style>

<template>
    <div v-bind:style="{ backgroundColor: colour, height: height }" v-on:click="clicked()"></div>
</template>

<script>
    export default {
        name: 'colourSquare',
        props: {
            height: String
        },
        methods: {
            clicked() {
                this.$emit('clicked', this.colour);
            }
        },
        created() {
            let r = Math.floor(Math.random() * 255);
            let g = Math.floor(Math.random() * 255);
            let b = Math.floor(Math.random() * 255);

            let rgb = 'rgb(' + r + ', ' + g + ', ' + b + ')';
            this.colour = rgb;
            this.$emit('colour', this.colour);
        },
        data() {
            return {
                colour: '',
                heightSq: ''
            }
        }
    }
</script>
