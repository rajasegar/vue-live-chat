<template>
  <div class="sc-new-messsages-count" v-if="count > 0">
      {{ count }}
    </div>
</template>
<script>
  export default {
  name: 'MessageCount',
  props: {
  count: String
  }
  }
</script>

<style scoped>
.sc-new-messsages-count {
  position: absolute;
  top: -3px;
  left: 41px;
  display: flex;
  justify-content: center;
  flex-direction: column;
  border-radius: 50%;
	width: 22px;
  height: 22px;
  background: #ff4646;
  color: white;
  text-align: center;
  margin: auto;
  font-size: 12px;
  font-weight: 500;
}
</style>
