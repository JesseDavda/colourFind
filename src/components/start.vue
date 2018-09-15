<style>
    
</style>

<template>
    <div>
        <h1>Find this colour:</h1>
        <h4>{{ this.props.startingColour }}</h4>
    <div>
</template>

<script>
    export default {
        name: 'start',
        props: {
            startingColour: String
        }
    }
</script>
