<template>
  <div style="border: 1px solid blue;">
    <p>
      <label>
        Ulica:<br>
        <input v-model="street" />
      </label>
    </p>
    <p>
      <label>
        Číslo popisné:<br>
        <input v-model="landNumber" />
      </label>
    </p>
    <p>
      <label>
        Číslo orientačné:<br>
        <input v-model="houseNumber" />
      </label>
    </p>
  </div>
</template>

<script>
/* eslint-disable */

const ADDRESS_RE = /^(.*) (\d*)([/]*)(\d*)$/

function joinNonEmpty (input = [], divider = ' ') {
  return input.filter(Boolean).join(divider)
}

export default {
  name: 'AddressEditor',
  data () {
    const {street, landNumber, houseNumber} = this.parseAddress(this.value)
    return {
      street,
      landNumber,
      houseNumber
    }
  },
  props: {
    value: {
      type: String,
      required: false,
      default: ''
    }
  },
  methods: {
    parseAddress (address, xxx) {
      /*
      console.log(ADDRESS_RE.exec('Ulica 123/456'))
      console.log(ADDRESS_RE.exec('Ulica 123'))
      console.log(ADDRESS_RE.exec('Ulica'))
      console.log(ADDRESS_RE.exec('Ulica dvojslovna 123/456'))
      console.log(ADDRESS_RE.exec('Ulica dvojslovna 123'))
      console.log(ADDRESS_RE.exec('Ulica 123/456 999'))
      console.log(ADDRESS_RE.exec('Ulica dvojslovna'))
      console.log(ADDRESS_RE.exec('123/456'))
      console.log(ADDRESS_RE.exec('123'))
      console.log(ADDRESS_RE.exec(''))
      console.log(ADDRESS_RE.exec('Ulica 123/456 xxx'))
      */

      const [, street = address, landNumber = '', , houseNumber = ''] = ADDRESS_RE.exec(address) || []

      return {
        street,
        landNumber,
        houseNumber
      }
    }
  },
  computed: {
    fullAddress () {
      const addressNumbers = joinNonEmpty([this.landNumber, this.houseNumber], '/')
      return joinNonEmpty([this.street, addressNumbers], ' ')
    }
  },
  watch: {
    value (newValue) {
      const {street, landNumber, houseNumber} = this.parseAddress(newValue)
      this.street = street
      this.landNumber = landNumber
      this.houseNumber = houseNumber
    },
    fullAddress (newValue) {
      this.$emit('input', newValue)
    }
  }
}
</script>

<style scoped>

</style>
