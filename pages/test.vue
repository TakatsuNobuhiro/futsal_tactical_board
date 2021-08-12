<template>
    <div id="app">
        <div class="of circle object" draggable="true" v-bind:style="{top: object1.top + 'px',left: object1.left + 'px'}" @mousedown="dragStart" @mousemove="drag" @mouseup="dragEnd" >1</div>

    </div>
</template>


<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
    data(){
        return{
            object1:{
                top: 500,
                left: 500,
                
            },
            mouse:{
                isDrag: false,
                top: 0,
                left: 0
    
            }
            

        }
    },
    methods: {
        drag :function(e){
            let y = e.pageY
            let x = e.pageX

            if(!this.mouse.isDrag) {
                return;
            }
            this.object1.top =  y - this.mouse.left
            this.object1.left =  x - this.mouse.top
            
        },
        dragStart:function(e){
            let x = e.layerX
            let y = e.layerY
            this.mouse.isDrag = true;
            this.mouse.left = x
            this.mouse.top = y
            
        },
        dragEnd: function(){
            this.mouse.isDrag = false;
        }
        

    }
})
</script>


<style scoped>
    .of{
        background-color:#ed230c;
        visibility: hidden;

    }
    .df{
        background-color:#09a1ff;
    }

    .circle{
        position:absolute;
        font-size:32px;
        width:50px;
        height:50px;
        color:white;
        text-align:center;
        font-weight:bold;
        border-radius:50%;

    }

    .object{
        cursor: move;
    }


</style>