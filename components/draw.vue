<template>
  <div>
    <div id="canvas-area">
      <canvas id="myCanvas" width="640px" height="800px" @mousedown="dragStart" @mouseup="dragEnd" @mouseout="dragEnd" @mousemove="draw"></canvas>
    </div>
  </div>
</template>

<style scoped>
#myCanvas {
 border: 1px solid #000000;
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
      this.context.lineWidth = 5;
      this.context.strokeStyle = '#000000';
  },
  methods: {
    // 描画
    draw :function(e) {
      var x = e.layerX
      var y = e.layerY
 
      if(!this.isDrag) {
        return;
      }
 
      this.context.lineTo(x, y);
      this.context.stroke();
    },
    // 描画開始（mousedown）
    dragStart:function(e) {
      var x = e.layerX
      var y = e.layerY
 
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