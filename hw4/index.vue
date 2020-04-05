<template>
  <div>
      <p>
        <b>Vyfiltruj jen pražské adresy:</b><br>
        <label><input type="checkbox" v-model="inPrague">Praha</label>
      </p>
      <p>
        <b>Seznam adres:</b><br>
            <ul>
                <span v-for="(address, index) in addresses" :key="index">
                    <li v-if="(inPrague == true && address.city == 'Praha') || (inPrague == false)">{{address.street + ', ' + address.city + ' ' + address.zip}}</li>
                </span>
            </ul>
      </p>
      <div>
        <b>Chybí ti nějaká adresa? Zde si ji můžeš přidat:</b><br>
        <form>
            <p>
                <label>
                    Ulice a číslo popisné:<br>
                    <input type="text" v-model="newAddress.street">
                </label>
            </p>
            <p>
                <label>
                    Město:<br>
                    <input type="text" v-model="newAddress.city">
                </label>
            </p>
            <p>
                <label>
                    PSČ:<br>
                    <input type="text" v-model="newAddress.zip">
                </label>
            </p>
            <p>
                <button @click.prevent="addAddress">Přidat adresu</button>
            </p> 
        </form>                           
      </div>
  </div>    
</template>

<script>
export default {
    data() {
        return {
            addresses: 
                [{
                    street: 'Makarská 10',
                    city: 'Brno',
                    zip: '28802'
                },
                {
                    street: 'Návštěvník 1569/10',
                    city: 'Praha',
                    zip: '28802'
                },
                {
                    street: 'Ostravská 1569/10',
                    city: 'Ostrava',
                    zip: '256697'
                }
                ],
            inPrague: false, 
            newAddress: {}  
        }
    },
    methods: {
        addAddress() {
            if(this.newAddress.street && this.newAddress.city && this.newAddress.zip) {
                this.addresses.push({...this.newAddress});
                this.newAddress = {};
            } else {
                alert('Před přidáním musí být vyplněna celá adresa!');
            }
        }
    }
}
</script>

<style>

</style>