<template>
  <div>
    <h1>This is the Peer Video Channel</h1>
    <form>
      <textarea id="incoming"></textarea>
      <button v-on:click="sendMessage">submit</button>
    </form>
    <pre id="outgoing"></pre>
  </div>
</template>
<script>
const Peer = require('simple-peer')
const peer = Peer()

peer.on('error', function (err) { console.log('error', err) })

peer.on('signal', function (data) {
  console.log('SIGNAL', JSON.stringify(data))
  document.querySelector('#outgoing').textContent = JSON.stringify(data)
})

peer.on('connect', function () {
  console.log('CONNECT')
  peer.send('whatever' + Math.random())
})
 
peer.on('data', function (data) {
  console.log('data: ' + data)
})

export default {
 methods: {
    sendMessage: function (event) {
      //peer.signal(JSON.parse(document.querySelector('#incoming').value))
      console.log("I am the the event", event)
    }
  } 
}
</script>
<style>
  #outgoing {
        width: 600px;
        word-wrap: break-word;
      }
</style>
