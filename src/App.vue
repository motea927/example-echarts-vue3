<template>
  <div ref="container" class="container">
  </div>
</template>

<script>
import { ref, onMounted } from 'vue'
import usePie from './composable/usePie'
export default {
  name: 'App',
  setup () {
    const container = ref(null)

    onMounted(() => {
      const { setOption, resize } = usePie(container.value)
      setOption([
        { value: 2200, name: '哆啦A夢', itemStyle: { color: '#46B3E6' } },
        { value: 2200, name: '小夫', itemStyle: { color: '#2E279D' } },
        { value: 4400, name: '胖虎', itemStyle: { color: '#4D80E4' } }
      ])
      window.addEventListener('resize', () => {
        resize()
      })
    })

    return { container }
  }
}
</script>

<style>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
html,
body {
  width: 100%;
  height: 100%;
  background-color: #e9e9e9;
  display: flex;
  justify-content: center;
  align-items: center;
}
#app {
  width: 100%;
  height: 100%;
  padding: 80px;
}
.container {
  width: 100%;
  height: 100%;
  background-color: #fff;
  border-radius: 5px;
}
</style>
