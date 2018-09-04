<template>
  <div class="sc-message--emoji">{{ message.data.emoji }}</div>
</template>

<script>
export default {
  name: 'EmojiMessage',
  props: {
    message: Object
  }

}
</script>

<style scoped>
  .sc-message--emoji {
  font-size: 40px;
}

</style>
