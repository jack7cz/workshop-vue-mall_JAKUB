<template>
  <div>
    <NameEditor :firstName="firstName" :lastName="lastName" />
  </div>
</template>

<script>
import NameEditor from './NameEditor'

export default {
  components: { NameEditor },
  data: function () {
    return {
      firstName: 'Riki',
      lastName: 'Fridrich',     
    }
  }
}
</script>

<style>

</style>
