<template>
    <div id="canvas-area">
        <VueDragResize  :aspectRatio="true" :isResizable="false" :isDraggable="false" :w="1900" :preventActiveBehavior="true" >
            <img src="/image/board.png" width="100%">
            <!-- red -->
            <VueDragResize v-on:dragging="resize" :aspectRatio="true" :isResizable="false" :w="50" :h="50" :x="450" :y="480" >
                <div  class="of circle object">1</div>
            </VueDragResize>
            <VueDragResize v-on:dragging="resize" :aspectRatio="true" :isResizable="false" :w="50" :h="50" :x="550" :y="150">
                <div  class="of circle object">2</div>
            </VueDragResize>
            <VueDragResize v-on:dragging="resize" :aspectRatio="true" :isResizable="false" :w="50" :h="50" :x="550" :y="810">
                <div  class="of circle object">3</div>
            </VueDragResize>
            <VueDragResize v-on:dragging="resize" :aspectRatio="true" :isResizable="false" :w="50" :h="50" :x="1300" :y="480">
                <div  class="of circle object">4</div>
            </VueDragResize>
            <VueDragResize v-on:dragging="resize" :aspectRatio="true" :isResizable="false" :w="50" :h="50" :x="150" :y="480">
                <div  class="of circle object">G</div>
            </VueDragResize>

            <!-- blue -->
            <VueDragResize v-on:dragging="resize" :aspectRatio="true" :isResizable="false" :w="50" :h="50" :x="600" :y="480">
                <div class="df circle object">1</div>
            </VueDragResize>
            <VueDragResize v-on:dragging="resize" :aspectRatio="true" :isResizable="false" :w="50" :h="50" :x="750" :y="230">
                <div class="df circle object">2</div>
            </VueDragResize>
            <VueDragResize v-on:dragging="resize" :aspectRatio="true" :isResizable="false" :w="50" :h="50" :x="750" :y="730">
                <div class="df circle object">3</div>
            </VueDragResize>
            <VueDragResize v-on:dragging="resize" :aspectRatio="true" :isResizable="false" :w="50" :h="50" :x="1400" :y="480">
                <div class="df circle object">4</div>
            </VueDragResize>
            <VueDragResize v-on:dragging="resize" :aspectRatio="true" :isResizable="false" :w="50" :h="50" :x="1700" :y="480"> 
                <div class="df circle object">G</div>
            </VueDragResize>

            <!-- ball -->
            <VueDragResize v-on:dragging="resize" :aspectRatio="true" :isResizable="false" :w="30" :h="30" :x="500" :y="510"> 
                <font-awesome-icon :icon="['fas', 'futbol']" size="2x" class="object" />

            </VueDragResize>
            
        </VueDragResize>

        
    </div>
</template>

<script>

    import VueDragResize from 'vue-drag-resize';


    

    export default {
            
        computed: {
            red_width(){
                let window_width = window.innerWidth 
                return window_width /3
            }
        },
        
        

        components: {

            VueDragResize
        },


    }
</script>

<style scoped>
    .of{
        background-color:#ed230c;
    }
    .df{
        background-color:#09a1ff;
    }

    .circle{
        font-size:32px;
        width:100%;
        height:100%;
        color:white;
        text-align:center;
        font-weight:bold;
        border-radius:50%;

    }

    .object{
        cursor: move;
    }
</style>