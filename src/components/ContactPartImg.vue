<template>
  <div class="mb-5">
    <div class="pt-5 pb-3" id="content-cu-eng">
      <img
        :src="require(`@/assets/${img}`)"
        alt="Chula Engineering"
        style="display: block; margin-left: auto; margin-right: auto; max-height: 200px; max-width: 50vw;"
      />
    </div>
    <h2 class="my-display-1 pt-4" style="text-align: center;">{{ name }}</h2>
  </div>
</template>
<script>
import { makeRe } from 'minimatch'
export default {
  name: 'ContactPart',
  props: {
    name: String,
    img: String
  },
  data: () => ({}),
  computed: {},
  methods: {}
}
</script>
<style scoped>
p {
  font-size: 1.3rem;
}
li {
  font-size: 1.2rem;
}
</style>