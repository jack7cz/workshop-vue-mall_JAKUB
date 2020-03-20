<template>
  <div>
    <p>
      {{ value }}
    </p>
  </div>
</template>

<script>
export default {
  name: 'Value',
  data () {
    return {
    }
  },
  props: {
    value: {
      type: String,
      default: 'Hodnota'
    } 
  }
}
</script>

<style scoped>

</style>
