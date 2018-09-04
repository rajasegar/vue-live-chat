<template>
  <div class="sc-message-list"  >
    <template v-for="message in messages">
          <Message :message=message  />
    </template>
      </div>
</template>

<script>
  import Message from './Message.vue';

  export default {
    name: 'MessageList',
    components: {
      Message
    },
    props: {
      messages: Array
    },
    data: function() {
      return {
      }
    },
  }
</script>

<style scoped>
  .sc-message-list {
  height: 80%;
  overflow-y: auto;
  background-color: white;
  background-size: 100%;
  padding: 40px 0px;
}
</style>
