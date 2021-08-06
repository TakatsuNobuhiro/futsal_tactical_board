<template>
  <div>
    <div id="canvas-area">
      <canvas id="myCanvas" width="100%" height="100%" @mousedown="dragStart" @mouseup="dragEnd" @mouseout="dragEnd" @mousemove="draw"></canvas>
    </div>
  </div>
</template>

<style scoped>
.canvas-area{
  position: absolute;
}

#myCanvas {
 border: 1px solid #000000;
 z-index: 100;


}

</style>

<script>
export default {
  name: "DrawTool",
  data() {
    return {
        canvas: null,
        context: null,
        isDrag: false
    };
  },
  mounted(){
      this.canvas = document.querySelector('#myCanvas')
      this.context = this.canvas.getContext('2d')
      this.context.lineCap = 'round';
      this.context.lineJoin = 'round';
      this.context.lineWidth = 10;
      this.context.strokeStyle = '#000000';

    　this.canvas.setAttribute('width',window.innerWidth)
    　this.canvas.setAttribute('height',window.innerHeight)

  },
  methods: {
    // 描画
    draw :function(e) {
      let x = e.layerX
      let y = e.layerY
 
      if(!this.isDrag) {
        return;
      }
 
      this.context.lineTo(x, y);
      this.context.stroke();
    },
    // 描画開始（mousedown）
    dragStart:function(e) {
      let x = e.layerX
      let y = e.layerY
 
      this.context.beginPath();
      this.context.lineTo(x, y);
      this.context.stroke();
   
      this.isDrag = true;
    },
    // 描画終了（mouseup, mouseout）
    dragEnd: function() {
      this.context.closePath();
      this.isDrag = false;
    }
  }
};
</script>