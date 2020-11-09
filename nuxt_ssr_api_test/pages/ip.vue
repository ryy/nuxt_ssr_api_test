<template>
  <div>
    {{ ip }}
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      ip: ""
    }
  },
  async asyncData({ $axios }) { // asyncData という nuxt 特有の機能において
    const ip = await $axios.$get('http://icanhazip.com')
    return { ip }
  }
}
</script>