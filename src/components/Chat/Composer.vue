<template>
  <form class="flex flex-row flex-space-between" id="send-message" v-on:submit.prevent>
    <input type="text" name="text" class="flex flex-1" v-model="newMessage">
    <button class="button-primary" type="submit" @click="addMessage">Send</button>
  </form>
</template>

<script>
export default {
  name: 'MessageComposer',
  props: {
    createMessage: Function
  },
  data: () => ({
    newMessage: ''
  }),
  methods: {
    addMessage () {
      // Create a new message and then clear the input field
      this.createMessage({ text: this.newMessage }).then(this.clearMessage)
    },
    clearMessage () {
      this.newMessage = ''
    }
  }
}
</script>
