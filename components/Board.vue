<template>
    <div id="board">
        <VueDragResize  :aspectRatio="true" :isResizable="false" :isDraggable="false"  :preventActiveBehavior="true" >

            <!-- red -->
            <VueDragResize v-for="red_object in red_objects" :key="red_object.index" v-on:dragging="resize" :aspectRatio="true" :isResizable="false" :w="50" :h="50" :x=red_object.x :y=red_object.y >
                <div  class="of circle object">{{red_object.index}}</div>
            </VueDragResize>


            <!-- blue -->
            <VueDragResize v-for="blue_object in blue_objects" :key="blue_object.index" v-on:dragging="resize" :aspectRatio="true" :isResizable="false" :w="50" :h="50" :x=blue_object.x :y=blue_object.y>
                <div class="df circle object">{{blue_object.index}}</div>
            </VueDragResize>
            <!-- <VueDragResize v-on:dragging="resize" :aspectRatio="true" :isResizable="false" :w="50" :h="50" :x="750" :y="230">
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
            </VueDragResize> -->

            <!-- ball -->
            <VueDragResize v-on:dragging="resize" :aspectRatio="true" :isResizable="false" :w="30" :h="30" :x=ball.x :y=ball.y> 
                <font-awesome-icon :icon="['fas', 'futbol']" size="2x" class="object" />
            </VueDragResize>
            
        </VueDragResize>
        <Draw />


        
    </div>
</template>

<script>

    import VueDragResize from 'vue-drag-resize';


    

    export default {
        data(){
            return{
                red_objects:{
                    red_1:{
                        index:"1",
                        x:450,
                        y:480
                    },
                    red_2:{
                        index:"2",
                        x:550,
                        y:150
                    },
                    red_3:{
                        index:"3",
                        x:550,
                        y:810
                    },
                    red_4:{
                        index:"4",
                        x:1300,
                        y:480
                    },
                    red_g:{
                        index:"G",
                        x:150,
                        y:480
                    }
                },
                blue_objects:{
                    blue_1:{
                        index:"1",
                        x:600,
                        y:480
                    },
                    blue_2:{
                        index:"2",
                        x:750,
                        y:230
                    },
                    blue_3:{
                        index:"3",
                        x:750,
                        y:730
                    },
                    blue_4:{
                        index:"4",
                        x:1400,
                        y:480
                    },
                    blue_g:{
                        index:"G",
                        x:1700,
                        y:480
                    },
                },
                ball:{
                    x:500,
                    y:510
                }
            
            }
            
        },
            
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

    #board{
        position:absolute;
        top:0;
        background-size: cover;
        background-image: url("/image/board.png");
    }

</style>