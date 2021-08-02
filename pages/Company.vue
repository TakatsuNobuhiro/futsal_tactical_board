<template>
    <div id="app">
        <img src="/image/board.png" width="1500px">
        <!-- red -->
        <VueDragResize v-on:dragging="resize" :aspectRatio="true" :isResizable="false" :w="50" :h="50">
            <div id="red-circle">1</div>
        </VueDragResize>
        <VueDragResize v-on:dragging="resize" :aspectRatio="true" :isResizable="false" :w="50" :h="50">
            <div id="red-circle">2</div>
        </VueDragResize>
        <VueDragResize v-on:dragging="resize" :aspectRatio="true" :isResizable="false" :w="50" :h="50">
            <div id="red-circle">3</div>
        </VueDragResize>
        <VueDragResize v-on:dragging="resize" :aspectRatio="true" :isResizable="false" :w="50" :h="50">
            <div id="red-circle">4</div>
        </VueDragResize>
        <VueDragResize v-on:dragging="resize" :aspectRatio="true" :isResizable="false" :w="50" :h="50">
            <div id="red-circle">5</div>
        </VueDragResize>

        <!-- blue -->
        <VueDragResize v-on:dragging="resize" :aspectRatio="true" :isResizable="false" :w="50" :h="50" :x="100">
            <div id="blue-circle">1</div>
        </VueDragResize>
        <VueDragResize v-on:dragging="resize" :aspectRatio="true" :isResizable="false" :w="50" :h="50" :x="100">
            <div id="blue-circle">2</div>
        </VueDragResize>
        <VueDragResize v-on:dragging="resize" :aspectRatio="true" :isResizable="false" :w="50" :h="50" :x="100">
            <div id="blue-circle">3</div>
        </VueDragResize>
        <VueDragResize v-on:dragging="resize" :aspectRatio="true" :isResizable="false" :w="50" :h="50" :x="100">
            <div id="blue-circle">4</div>
        </VueDragResize>
        <VueDragResize v-on:dragging="resize" :aspectRatio="true" :isResizable="false" :w="50" :h="50" :x="100"> 
            <div id="blue-circle">5</div>
        </VueDragResize>
    </div>
</template>

<script>
    import VueDragResize from 'vue-drag-resize';

    export default {

        
        name: 'app',

        components: {
            VueDragResize
        },


    }
</script>

<style scoped>
    #red-circle{
        font-size:30px;
        width:100%;
        height:100%;

        background-color:tomato;
        color:white;
        text-align:center;

        border-radius:50%;
    }
    #blue-circle{
        font-size:30px;
        width:100%;
        height:100%;

        background-color:blue;
        color:white;
        text-align:center;

        border-radius:50%;
    }
</style>
