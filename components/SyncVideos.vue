<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const props = defineProps({
  names: { type: Array, required: true },
  start: { type: Number, default: 5 },
  end: { type: Number, default: 10 },
})

const root = ref(null)
const base = import.meta.env.BASE_URL
let timer

onMounted(async () => {
  const vids = [...root.value.querySelectorAll('video')]

  await Promise.all(
    vids.map(v => {
      if (v.readyState >= 1) return Promise.resolve()

      return new Promise(resolve => {
        v.addEventListener('loadedmetadata', resolve, { once: true })
        v.addEventListener('error', resolve, { once: true })
      })
    })
  )

  vids.forEach(v => {
    v.currentTime = props.start
    v.play().catch(() => {})
  })

  timer = setInterval(() => {
    vids.forEach(v => {
      if (v.error || v.readyState < 1) return

      if (v.currentTime >= props.end) {
        v.currentTime = props.start
        if (v.paused) v.play().catch(() => {})
      }
    })
  }, 100)
})

onUnmounted(() => clearInterval(timer))
</script>

<template>
  <div ref="root" class="grid grid-cols-8 gap-1">
    <video
      v-for="n in names"
      :key="n"
      :src="`${base}${n}.mp4`"
      autoplay
      muted
      playsinline
      preload="auto"
      class="w-full aspect-square object-cover"
    />
  </div>
</template>