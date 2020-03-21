<template>
    <div style="border: 1px solid blue;">
        <p>
            Street
            <input type="text" v-model="street"/>
        </p>
        <p>
            Land Registry Number
            <input type="text" v-model="landNum"/>
        </p> 
        <p>
            House Number
            <input type="text" v-model="houseNum"/>
        </p> 
            {{ wholeAddress }}                   
    </div>
</template>

<script>
export default {
    name: 'AddressEditor',
    data() {
        let regAddress = /^(.*) (\d*)([/]*)(\d*)$/.exec(this.value);        
        return {
            street: regAddress[1] ? regAddress[1] : '',
            landNum: regAddress[2] ? regAddress[2] : '',
            houseNum: regAddress[4] ? regAddress[4] : ''
        }
    },
    props: {
        value: {
            type: String,
            default: 'U garáží 1611/1 (2)'
        }
    },
    watch: {
        wholeAddress() {
            this.setWholeAddress()
        },
        value () {
         //console.log('value', this.value)
         let regAddress = /^(.*) (\d*)([/]*)(\d*)$/.exec(this.value); 

         this.street = regAddress ? regAddress[1] : this.value;
         this.landNum = (regAddress && regAddress[2]) ? regAddress[2] : '';
         this.houseNum = (regAddress && regAddress[4]) ? regAddress[4] : ''; 

         //console.log('this.street', this.street); 
         //console.log('this.landNum', this.landNum); 
         //console.log('this.houseNum', this.houseNum); 
        }
    },
    computed: {
        wholeAddress() {
            let numPart = [this.landNum, this.houseNum]
                        .filter((item) => item !== '')
                        .join('/');
                        //console.log('numPart', numPart);
            return [this.street, numPart]
                        .filter((item) => item !== '')
                        .join(' ');
        }
    },
    methods: {
    setWholeAddress () {
      this.$emit('input', this.wholeAddress)
    }
  }
}
</script>

<style scoped>

</style>