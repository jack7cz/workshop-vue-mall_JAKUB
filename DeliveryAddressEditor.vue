<template>
    <div>
        <name-editor v-model="value.name"></name-editor>
        <address-editor v-model="value.address"></address-editor>
          <div class="green-border">
            <p>
            city:
            <input v-model="value.city" />
            </p>
            <p>
            zip code:
            <input v-model="value.zip" />
            </p>
         </div>
    </div>   
</template>
<script>
import NameEditor from './NameEditor'
import AddressEditor from './AddressEditor'
export default {
    components: { AddressEditor, NameEditor }, 
    props: {
        value: {
            type: Object,
            default() {
                return {
                    name: 'Johnatan Doedoe',
                    address: 'U garáží 1611/1',
                    city: 'Praha',
                    zip: '17000'
                }
            }    
        }
    }  
}
</script>
<style scoped>
    .green-border {
        border: 1px solid green;
    }
</style>