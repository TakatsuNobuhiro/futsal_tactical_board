<template>
    <div id="board">

        <VueDragResize  :aspectRatio="true" :isResizable="false" :isDraggable="false"  :preventActiveBehavior="true" >

            <!-- red -->
            <VueDragResize v-for="red_object in red_objects" :key="red_object.id"  :aspectRatio="true" :isResizable="false" :w="50" :h="50" :x=red_object.x :y=red_object.y >
                <div  class="of circle object">{{red_object.name}}</div>
            </VueDragResize>


            <!-- blue -->
            <VueDragResize v-for="blue_object in blue_objects" :key="blue_object.index" :aspectRatio="true" :isResizable="false" :w="50" :h="50" :x=blue_object.x :y=blue_object.y>
                <div class="df circle object">{{blue_object.name}}</div>
            </VueDragResize>

            <!-- ball -->
            <VueDragResize :aspectRatio="true" :isResizable="false" :w="30" :h="30" :x=ball.x :y=ball.y> 
                <font-awesome-icon :icon="['fas', 'futbol']" size="2x" class="object" />
            </VueDragResize>
            
        </VueDragResize>
        <Draw />
        <div class="btn btn-danger btn-sm" @click="formation_3_1">3-1</div>
        <div class="btn btn-danger btn-sm" @click="formation_4_0">4-0</div>
        <p>{{ball.x}}</p>
        <p>{{ball.y}}</p>
    </div>
</template>

<script>

    import VueDragResize from 'vue-drag-resize';

    export default {
        data(){
            return{
                red_objects:{
                    red_1:{
                        index:"r1",
                        name:"1",
                        x:450,
                        y:480
                    },
                    red_2:{
                        index:"r2",
                        name:"2",
                        x:550,
                        y:150
                    },
                    red_3:{
                        index:"r3",
                        name:"3",
                        x:550,
                        y:810
                    },
                    red_4:{
                        index:"r4",
                        name:"4",
                        x:1300,
                        y:480,
                    },
                    red_g:{
                        index:"rG",
                        name:"G",
                        x:150,
                        y:480
                    }
                },
                blue_objects:{
                    blue_1:{
                        index:"b1",
                        name:"1",
                        x:600,
                        y:480
                    },
                    blue_2:{
                        index:"b2",
                        name:"2",
                        x:750,
                        y:230
                    },
                    blue_3:{
                        index:"b3",
                        name:"3",
                        x:750,
                        y:730
                    },
                    blue_4:{
                        index:"b4",
                        name:"4",
                        x:1400,
                        y:480
                    },
                    blue_g:{
                        index:"bG",
                        name:"G",
                        x:1700,
                        y:480
                    },
                },
                ball:{
                    x:500,
                    y:500
                }
            
            }
            
        },
            
        methods: {
            handleResize: function(){
                this.window_size.width = window.innerWidth,
                this.window.height = window.innerHeight
            },
            calc :function(x,y){
                let window_width = window.innerWidth
                let board_width = window_width - 230
                let board_height = board_width / 2 
                let board_x = board_width * x  + 100
                let board_y = board_height * y + 50
             
                return [board_x,board_y]
            },
            formation_3_1 :function(){
                let p_ls = this.calc(0.23,0)
                // this.ball = { x: p_ls[0],y: p_ls[1]}
                this.$set(this.ball,"x",p_ls[0])


                setTimeout(alert("aaa"),30000)
                this.$set(this.ball,"y",p_ls[1])
                this.ball = Object.assign({}, this.ball, {x: p_ls[0],y: p_ls[1]})


                console.log(p_ls)
                


                let red_1_ls = this.calc(0.23,0.9)
                this.red_objects.red_1.x = red_1_ls[0]
                this.red_objects.red_1.y = red_1_ls[1]
            

                let red_2_ls = this.calc(0.3,0.1)
                this.red_objects.red_2.x = red_2_ls[0]
                this.red_objects.red_2.y = red_2_ls[1]


                let red_3_ls = this.calc(0.3,0.9)
                this.red_objects.red_3.x = red_3_ls[0]
                this.red_objects.red_3.y = red_3_ls[1]

                let red_4_ls = this.calc(0.75,0.1)

                this.red_objects.red_4 = {
                                            index:"r4",
                                            name:"4",
                                            x:red_4_ls[0],
                                            y:red_4_ls[1],
                                        }

                

                let red_g_ls = this.calc(0.05,0.5)
                this.red_objects.red_g.x = red_g_ls[0]
                this.red_objects.red_g.y = red_g_ls[1]

                this.$forceUpdate();


            },
            formation_4_0 :function(){
                let p_ls = this.calc(0.23,0.9)
                this.ball = { x: p_ls[0],y: p_ls[1]}
              

                let red_1_ls = this.calc(0.22,0.25)
                this.red_objects.red_1.x = red_1_ls[0]
                this.red_objects.red_1.y = red_1_ls[1]

                let red_2_ls = this.calc(0.3,0.1)
                this.red_objects.red_2.x = red_2_ls[0]
                this.red_objects.red_2.y = red_2_ls[1]

                let red_3_ls = this.calc(0.3,0.9)
                this.red_objects.red_3.x = red_3_ls[0]
                this.red_objects.red_3.y = red_3_ls[1]
                

                let red_4_ls = this.calc(0.22,0.75)
                this.red_objects.red_4.x = red_4_ls[0]
                this.red_objects.red_4.y = red_4_ls[1]
                console.log(red_4_ls)
  

                let red_g_ls = this.calc(0.05,0.5)
                this.red_objects.red_g.x = red_g_ls[0]
                this.red_objects.red_g.y = red_g_ls[1]


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
        width:100%;

        position:absolute;
        top:0;
        background-size: contain;
        background-repeat: no-repeat;
        background-image: url("/image/board.png");
    }

</style>