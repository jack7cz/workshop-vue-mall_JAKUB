<template>
  <div>
    <Value :value="value1"/>
  </div>
</template>

<script>
import Value from './value'

export default {
  components: { Value },
  data: function () {
    return {
      value1: 'hodnota z index 2'
    }
  }
}
</script>

<style>

</style>
