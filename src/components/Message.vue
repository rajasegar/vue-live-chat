<template>
  <div class="sc-message">
        <div class="sc-message--content" :class="[message.author === 'me' ? 'sent' : 'received']">
          <div class="sc-message--avatar" :style="{ backgroundImage: `url(${chatIconUrl})`}">
          </div>
          <TextMessage v-if="textMessage" :message=message />
          <EmojiMessage v-if="emojiMessage" :message=message />
        </div>
      </div>
</template>

<script>
  import TextMessage from './TextMessage.vue';
  import EmojiMessage from './EmojiMessage.vue';

  export default {
    name: 'Message',
    components: {
      TextMessage, EmojiMessage
    },

    props: {
      message: Object
    },

    data: function() {
      return {
        chatIconUrl: '../assets/chat-icon.svg'
      }
    },

    computed: {
      textMessage: function() {
        return this.message.type === 'text';
      },

      emojiMessage: function() {
        return this.message.type === 'emoji';
      }

    }


  }

</script>

<style scoped>
  .sc-message {
  width: 300px;
  margin: auto;
  padding-bottom: 10px;
  display: flex;
}

.sc-message--content {
  width: 100%;
  display: flex;
}

.sc-message--content.sent {
  justify-content: flex-end;
}

.sc-message--content.sent .sc-message--avatar {
  display: none;
}

.sc-message--avatar {
  background-image: url(https://d13yacurqjgara.cloudfront.net/assets/avatar-default-aa2eab7684294781f93bc99ad394a0eb3249c5768c21390163c9f55ea8ef83a4.gif);
  background-repeat: no-repeat;
  background-size: 100%;
  background-position: center;
  min-width: 30px;
  min-height: 30px;
  border-radius: 50%;
  align-self: center;
  margin-right: 15px;
}

</style>
