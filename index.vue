<template>
  <div>
    <p>{{ deliveryAddress }}</p>
    <DeliveryAddressEditor v-model="deliveryAddress" />
  </div>
</template>

<script>

/*
ÚKOL

Vytvorte komponentu DeliveryAddressEditor pre editáciu dodcej adresy, ktorú dostanete vo formáte:

{
  name: 'John Doe',
  address: 'U garáží 1611/1',
  city: 'Praha',
  zip: '17000'
}

Zrecyklujte editory adresy a mena.
*/

import DeliveryAddressEditor from './DeliveryAddressEditor'

export default {
  components: { DeliveryAddressEditor },
  data: function () {
    return {
      deliveryAddress: {
        name: 'Johnik Doeik',
        address: 'U garáží 1611/1',
        city: 'Praha',
        zip: '17000'
      }
    }
  }
}
</script>

<style>

</style>
