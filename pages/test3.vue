<template>
    <div id="app">
        <VueDragResize :aspectRatio="true" :isResizable="false" :w="30" :h="30"> 
            <font-awesome-icon :icon="['fas', 'futbol']" size="2x" class="object" />
        </VueDragResize>

        <div class="btn btn-danger btn-sm" @click="revise">変更</div>

    </div>
    
</template>

<script>

    import VueDragResize from 'vue-drag-resize';


    

    export default {
        data(){
            return{
                ball:{
                    x:500,
                    y:500
                }
            }
        },
        methods:{
            revise :function(){
                // this.ball.y=1000
                // this.ball.x=1000
                this.ball = Object.assign({}, this.ball, {x: 100,y: 100})



            }
            

        },


        components: {

            VueDragResize
        }
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
        width:100%;

        position:absolute;
        top:0;
        background-size: contain;
        background-repeat: no-repeat;
        background-image: url("/image/board.png");
    }

</style>