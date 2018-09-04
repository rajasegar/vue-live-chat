<template>
  <div class="sc-chat-window" :class="[ open ? 'opened' : 'closed' ]">
    <Header
      :teamName=agentProfile.teamName
      :imageUrl=agentProfile.imageUrl
      :onClose=onClose />
          <MessageList
            :messages=messageList
            :imageUrl=agentProfile.imageUrl
          />
          <UserInput :showEmoji=showEmoji v-on:send-message="submitMessage" />
        </div>
</template>

<script>
import Header from './Header.vue';
import MessageList from './MessageList.vue';
import UserInput from './UserInput.vue';


export default {
  name: 'ChatWindow',
  
  components: {
    Header, MessageList, UserInput
  },
  
  data: function() {
    return {
    }
  },
  
  computed: {
    open: {
    get: function() {
      return this.isOpen;
    }
    }


  },
  props: {
  agentProfile: Object,
  showEmoji: Boolean,
    messageList: Array,
    isOpen: Boolean,
    onClose: Function
  },

  methods: {
    submitMessage: function(e) {
      this.$emit('send-message', e);
    }
  }



  }

</script>

<style scoped>
  .sc-chat-window {
  width: 370px;
  height: calc(100% - 120px);
  max-height: 590px;
  position: fixed;
  right: 25px;
  bottom: 100px;
  box-sizing: border-box;
  box-shadow: 0px 7px 40px 2px rgba(148, 149, 150, 0.3);
  background: white;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  transition: 0.3s ease-in-out;
  border-radius: 10px;
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
}

.sc-chat-window.closed {
  opacity: 0;
  visibility: hidden;
  bottom: 90px;
}

</style>
