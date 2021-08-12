<template>
    <div id="app">
        <h2>オブジェクト</h2>
        <p>y:{{object1.top}}</p>
        <p>x:{{object1.left}}</p>
        <div class="of circle object" v-bind:style="{top: this.object1.top + 'px',left: this.object1.left + 'px'}" @mousedown="dragStart" @mousemove="drag" @mouseup="dragEnd" >1</div>

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
            let x = e.clientX
            let y = e.clientY
            let dif_x = x - this.mouse.left
            let dif_y = y - this.mouse.top

            if(!this.mouse.isDrag) {
                return;
            }
            this.mouse.left = x
            this.mouse.top = y
            this.object1.left =  this.object1.left + dif_x
            this.object1.top =  this.object1.top + dif_y
            
        },
        dragStart:function(e){
            let x = e.clientX
            let y = e.clientY
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