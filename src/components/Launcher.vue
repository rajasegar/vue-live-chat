<template>
<div>
  
  <div class="sc-launcher" :class="{ 'opened' : open }" @click="handleClick">
    <MessageCount />
          <img class="sc-open-icon" src="../assets/close-icon.png" />
          <img class="sc-closed-icon" src="../assets/logo-no-bg.svg" />
        </div>
  <ChatWindow
    :agentProfile=agentProfile
    :isOpen=open
    :showEmoji=showEmoji
    :messageList=messageList
    :onClose="handleClick"
    v-on:send-message="newMessage"

    />
      </div>
</template>

<script>
  import MessageCount from './MessageCount.vue';
  import ChatWindow from './ChatWindow.vue';

export default {
  name: 'Launcher',
  components: {
    MessageCount, ChatWindow
  },
  props: {
  showEmoji: Boolean,
  isOpen: Boolean,
  messageList: Array,
  agentProfile: Object
  },
  data: function() {
    return {
  open: this.isOpen

    }
  },

  

  methods: {
    handleClick: function() {
      this.open = !(this.open);

  },

  newMessage: function(e) {
  this.$emit('new-message', e);
  }


  }
}
 </script>

<style scoped>
.sc-launcher {
  width: 60px;
  height: 60px;
  background-color: #4e8cff;
  background-position: center;
  background-repeat: no-repeat;
  position: fixed;
  right: 25px;
  bottom: 25px;
  border-radius: 50%;
  box-shadow: none;
  transition: box-shadow 0.2s ease-in-out;
}

.sc-launcher:before {
  content: '';
  position: relative;
  display: block;
  width: 60px;
  height: 60px;  
  border-radius: 50%;
  transition: box-shadow 0.2s ease-in-out;
}

.sc-launcher .sc-open-icon,
.sc-launcher .sc-closed-icon {
  width: 60px;
  height: 60px;
  position: fixed;
  right: 25px;
  bottom: 25px;
  transition: opacity 100ms ease-in-out, transform 100ms ease-in-out;
}

.sc-launcher .sc-closed-icon {
  transition: opacity 100ms ease-in-out, transform 100ms ease-in-out;
  width: 60px;
  height: 60px;
}

.sc-launcher .sc-open-icon {
  padding: 20px;
  box-sizing: border-box;
  opacity: 0;
}

.sc-launcher.opened .sc-open-icon {
  transform: rotate(-90deg);
  opacity: 1;
}

.sc-launcher.opened .sc-closed-icon {
  transform: rotate(-90deg);
  opacity: 0;
}

.sc-launcher.opened:before {
  box-shadow: 0px 0px 400px 250px rgba(148, 149, 150, 0.2);
}

.sc-launcher:hover {
  box-shadow: 0 0px 27px 1.5px rgba(0,0,0,0.2);
}
</style>
