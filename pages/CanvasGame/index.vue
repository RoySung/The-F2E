<template>
  <div id="canvas-game-page">
    <canvas ref="gameCanvas"></canvas>
  </div>
</template>

<script>
  export default {
    name: "CanvasGame",
    mounted() {
      const FPS = 30
      const canvas = this.$refs.gameCanvas
      const ctx = canvas.getContext('2d')
      const ww = window.innerWidth
      const wh = window.innerHeight
      const bgColor = 'black'
      canvas.width = ww
      canvas.height = wh

      const degreeToPI = (d) => d * Math.PI / 180
      const save = (handle) => {
        ctx.save()
        ctx.beginPath()
        handle()
        ctx.closePath()
        ctx.restore()
      }
      const drawMap = () => {
        ctx.strokeStyle = 'rgba(255, 255, 255, 0.5)'
        for (let i = 0; i <= 10; i++) {
          ctx.moveTo(i * ww / 10, 0)
          ctx.lineTo(i * ww / 10, wh)
        }
        for (let i = 0; i <= wh; i += ww / 10) {
          ctx.moveTo(0, i)
          ctx.lineTo(ww, i)
        }
        ctx.stroke()
      }
      const drawShip = () => {
        ctx.strokeStyle = 'white'
        ctx.lineWidth = 5
        ctx.shadowColor = 'white'
        ctx.shadowBlur = 10
        ctx.translate(ww / 2, wh / 2)
        ctx.arc(0, 0, 80, 0, degreeToPI(360))
        ctx.stroke()
        ctx.fillStyle = 'white'
        ctx.fillRect(80, -15, 30, 30)
      }
      const drawGame = () => {
        save(() => {
          ctx.fillStyle = bgColor
          ctx.fillRect(0, 0, ww, wh)
        })

        save(drawMap)
        save(drawShip)
      }

      const timer = setInterval(drawGame, 1000 / FPS)

    },
  }
</script>

<style lang="sass" src="./style.sass" scoped>

</style>
