<template>
  <h1>Name:{{ passenger.first_name }} {{ passenger.last_name }}</h1>
  <p>
    address: {{ passenger.ip_address }} on {{ passenger.Source }} @
    {{ passenger.Destination }}
  </p>
  <p>{{ passenger.travelDate }}</p>
  <button @click="detail">Update the passenger</button>
</template>
<script>
export default {
  props: ['passenger'],
  inject: ['GStore'],
  methods: {
    detail() {
      this.GStore.flashMessage = 'You are successfully edited details '
      setTimeout(() => {
        //After 3 seconds remove it
        this.GStore.flashMessage = ''
      }, 5000)
      this.$router.push({
        name: 'home'
      })
    }
  }
}
</script>
