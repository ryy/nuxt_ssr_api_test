<template>
  <div>

    <p>
      <a href="https://uncle-javascript.com/weird-nuxt-3-axios-data-fetch" target="_blank">@see ここが変だよ Nuxt.js: No.3 axions の設定、SSR のためのデータのフェッチ</a>
    </p>

    <br>
    <pre>
      async asyncData({ $axios }) {
        const ip = await $axios.$get('http://icanhazip.com')
        return { ip }
      }
    </pre>
    <p>
      IP: {{ip}}
    </p>

    <hr>

    <pre>
      methods: {
        async fetchSomething() {
          const ip = await this.$axios.$get('http://icanhazip.com')
          this.ip2 = ip
        }
      }
    </pre>
    <p>
      IP: {{ip2}}
    </p>

  </div>
</template>

<script>
export default {
  data: function () {
    return {
      ip: "",
      ip2: ""
    }
  },
  async asyncData({ $axios }) {
    const ip = await $axios.$get('http://icanhazip.com')
    return { ip }
  },
  methods: {
    async fetchSomething() {
      const ip = await this.$axios.$get('http://icanhazip.com')
      this.ip2 = ip
    }
  },
  created: function () {
    this.fetchSomething()
  }
}
</script>