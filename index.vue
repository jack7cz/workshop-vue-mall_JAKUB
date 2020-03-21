<template>
  <div>
    <h3>Name editor</h3>
    <p>{{ fullName }}</p>
    <p>
      Full name:
      <input type="text" v-model="fullName">
    </p>
    <NameEditor v-model="fullName" />

    <h3>Address editor</h3>
    <p>{{ address }}</p>
    <p>
      Whole address:
      <input type="text" v-model="address">
    </p>
    <AddressEditor v-model="address"/>
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
import AddressEditor from './AddressEditor'

export default {
  components: { NameEditor, AddressEditor },
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
