<template>
  <div>
    <p>
      First name:
      <input v-model="editableFirstName" />
      Last name:
      <input v-model="editableLastName" />      
    </p>
    <p><strong>Output:</strong><br/>
      {{ editableFirstName + ' ' + editableLastName }}
    </p>
  </div>
</template>

<script>
export default {
  name: 'NameEditor',
  data () {
    return {
      editableFirstName: this.firstName,
      editableLastName: this.lastName
    }
  },
  props: {
    firstName: {
      type: String,
      default: 'John'
    },
    lastName: {
      type: String,
      default: 'Doe'
    }    
  }
}
</script>

<style scoped>

</style>
