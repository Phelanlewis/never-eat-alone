<template>
  <h1>This is the Peer Video Channel</h1>
</template>
<script>
const Peer = require('simple-peer')
const peer = Peer()

peer.on('signal', (data) => {
  console.log(data)
})

export default {

}
</script>
<style>

</style>
