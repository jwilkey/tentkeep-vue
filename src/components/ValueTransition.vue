<template>
  <transition :name="transition">
    <div class="value-transition" v-if="display">{{ display }}</div>
  </transition>
</template>

<script>
export default {
  name: 'ValueTransition',
  data () {
    return {
      display: undefined
    }
  },
  props: ['value', 'name'],
  computed: {
    transition () {
      return this.name || 'fade'
    }
  },
  watch: {
    value () {
      this.display = undefined
      this.$nextTick(() => {
        this.display = this.value
      })
    }
  },
  mounted () {
    this.display = this.value
  }
}
</script>

<style lang="scss" scoped>
.value-transition {
  display: inline-block;
}
</style>
