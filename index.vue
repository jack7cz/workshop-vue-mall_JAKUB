<template>
  <div>
    <p>{{ fullName }}</p>
    <p>
      Full name:
      <input type="text" v-model="fullName">
    </p>
    <NameEditor v-model="fullName" />
  </div>
</template>

<script>

/*
ÚKOL

Vytvorte komponentu AddressEditor pre editáciu adresy, ktorú dostanete vo formáte:
U garáží 1611/1

Chceme zvlášť políčka pre ulicu, číslo popisné, číslo orientačné.
*/

import NameEditor from './NameEditor'

export default {
  components: { NameEditor },
  data: function () {
    return {
      fullName: 'Riki Fridrich',
      address: 'U garáží 1611/1'
    }
  }
}
</script>

<style>

</style>
