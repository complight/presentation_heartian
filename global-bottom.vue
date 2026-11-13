
<template>
  <div
    v-if="$slidev.nav.currentPage > 1 && $slidev.nav.currentPage < $slidev.nav.total"
    class="absolute bottom-3 right-5 text-xs text-white"
  >
    {{ $slidev.nav.currentPage }} / {{ $slidev.nav.total }}
  </div>
</template>
