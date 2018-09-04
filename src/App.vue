<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld :msg=msg v-on:new-message="pushMessage"/>
    <Launcher
      :agentProfile=agentProfile
      :messageList=messages
      :isOpen=isOpen
      :newMessagesCount=newMessagesCount
      :showEmoji=showEmoji
      v-on:new-message="pushMessage"
      />
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue';
import Launcher from './components/Launcher.vue';
import messageHistory from './messageHistory';

export default {
  name: 'app',
  components: {
    Launcher, HelloWorld
  },
  data: function() {
    return {
      msg: 'Vue Live Chat',
      messageList: messageHistory,
      newMessagesCount: 0,
      isOpen: false,
      agentProfile: {
        teamName: 'vue-live-chat',
        imageUrl: 'https://a.slack-edge.com/66f9/img/avatars-teams/ava_0001-34.png'
      },
      showEmoji: true
      
    }
  },
  
  computed: {
    messages: function() {
      return this.messageList;
    }
  },
  
  
  methods: {
    pushMessage: function(message) {
      let _messages = this.messageList;
      _messages.push(message);
      this.messageList = _messages;
      
      
    }
  }


}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
