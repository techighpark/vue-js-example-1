<template>
  <div>
    <h1>Lifecycle Test</h1>
  </div>
</template>

<script>
// const API_URL = `https://api.github.com/repos/vuejs/core/commits?per_page=3&sha=`
export default {
  name: "LifeCycleTest",
  data() {
    return {
      branches: ['main', 'v2-compat'],
      currentBranch: 'main',
      commits: null
    }
  },
  beforeCreate() {
    console.log('before created')
  },
  created() {
    console.log('created')
  },


  beforeMount() {
    console.log('before mounted')
  },
  mounted() {
    console.log('mounted')
  },
  computed: {
    computedFn() {
      console.log('computed' + this.currentBranch)
      return ''
    }
  },
  methods: {
    methodsFn() {
      console.log('methods')
    }
  },
  watch: {
    // currentBranch: 'fetchData'
  },
}
</script>

<style scoped>

</style>