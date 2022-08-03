<template>
  <h1>{{ passenger.gender }}</h1>
  <p>
    {{ passenger.ip_address }} on {{ passenger.Source }} @
    {{ passenger.Destination }}
  </p>
  <p>{{ passenger.travelDate }}</p>
</template>
<script>
export default {
  props: ['passenger']
}
</script>
