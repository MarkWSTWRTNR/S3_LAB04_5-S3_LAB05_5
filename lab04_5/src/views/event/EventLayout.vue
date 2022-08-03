<template>
  <div v-if="passenger">
    <div id="nav">
      <router-link :to="{ name: 'EventDetails', params: { id } }"
        >Details</router-link
      >
      |
      <!-- <router-link :to="{ name: 'EventRegister', params: { id } }"
        >Register</router-link
      > -->
    </div>
    <router-view :passenger="passenger" />
  </div>
</template>
<script>
import EventService from '@/service/EventService.js'
export default {
  props: ['id'],
  data() {
    return {
      passenger: null
    }
  },
  created() {
    EventService.getPassenger(this.id)
      .then((response) => {
        this.passenger = response.data
      })
      .catch((error) => {
        if (error.response && error.response.status == 404) {
          this.$router.push({
            name: '404Resource',
            params: { resource: 'passenger' }
          })
        } else {
          this.$router.push({ name: 'NetworkError' })
        }
      })
  }
}
</script>
