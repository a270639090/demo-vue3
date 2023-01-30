<template>
  <div class="about">
    <h1 @click="getMouse">This is an about page</h1>
  </div>
</template>

<script lang="ts" setup>
import { watch } from '@vue/runtime-core'
import { useMouse, usePreferredDark, useTitle } from '@vueuse/core'

const { x, y} = useMouse()
const getMouse = () => {
  console.log(x.value, y.value)
}

const isDark = usePreferredDark()

console.log('isDark',isDark.value)

const title = useTitle('Set title')

watch(isDark, () => {
  title.value = isDark.value ? '🌙 Good evening!' : '☀️ Good morning!'
})
</script>

<style lang="less">
h1 {
  width: 100%;
  height: 600px;
}
</style>
