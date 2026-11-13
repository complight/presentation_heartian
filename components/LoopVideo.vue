<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const props = defineProps({
  src: { type: String, required: true },
  start: { type: Number, default: 5 },
  end: { type: Number, default: 10 },
})

const video = ref(null)
let timer

onMounted(() => {
  const v = video.value
  const go = () => {
    v.currentTime = props.start
    v.play().catch(() => {})
  }
  if (v.readyState >= 1) go()
  else v.addEventListener('loadedmetadata', go, { once: true })
  timer = setInterval(() => {
    if (v.currentTime >= props.end) go()
  }, 50)
})

onUnmounted(() => clearInterval(timer))
</script>

<template>
  <video ref="video" :src="src" autoplay muted playsinline />
</template>