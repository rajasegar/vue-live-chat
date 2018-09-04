<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div class="demo-test-area--wrapper">
   <form class="demo-test-area">
  <div class="demo-test-area--preamble">Test the chat window by sending a message:</div>
  <textarea class="demo-test-area--text" placeholder="Write a test message...." v-model="message"></textarea>
  <button class="demo-test-area--button" @click="sendMessage"> Send Message! </button>
</form> 
   </div>
    <p>
      For guide and recipes on how to configure / customize this project,<br>
      check out the
      <a href="https://cli.vuejs.org" target="_blank" rel="noopener">vue-cli documentation</a>.
    </p>
    <h3>Installed CLI Plugins</h3>
    <ul>
      <li><a href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-babel" target="_blank" rel="noopener">babel</a></li>
      <li><a href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-eslint" target="_blank" rel="noopener">eslint</a></li>
    </ul>
    <h3>Essential Links</h3>
    <ul>
      <li><a href="https://vuejs.org" target="_blank" rel="noopener">Core Docs</a></li>
      <li><a href="https://forum.vuejs.org" target="_blank" rel="noopener">Forum</a></li>
      <li><a href="https://chat.vuejs.org" target="_blank" rel="noopener">Community Chat</a></li>
      <li><a href="https://twitter.com/vuejs" target="_blank" rel="noopener">Twitter</a></li>
      <li><a href="https://news.vuejs.org" target="_blank" rel="noopener">News</a></li>
    </ul>
    <h3>Ecosystem</h3>
    <ul>
      <li><a href="https://router.vuejs.org" target="_blank" rel="noopener">vue-router</a></li>
      <li><a href="https://vuex.vuejs.org" target="_blank" rel="noopener">vuex</a></li>
      <li><a href="https://github.com/vuejs/vue-devtools#vue-devtools" target="_blank" rel="noopener">vue-devtools</a></li>
      <li><a href="https://vue-loader.vuejs.org" target="_blank" rel="noopener">vue-loader</a></li>
      <li><a href="https://github.com/vuejs/awesome-vue" target="_blank" rel="noopener">awesome-vue</a></li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data: function() {
    return {
      message: ''
    }
  },
  
  props: {
    msg: String
  },
  
  methods: {
    sendMessage: function(e) {
      e.preventDefault();
      let text = this.message;
      let _message = {
        author: 'them',
        type: 'text',
        data: {
          text
        }
      };     
      this.$emit('new-message', _message);
      this.message = '';

    }
  }


}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
    margin: 40px 0 0;
}
ul {
    list-style-type: none;
    padding: 0;
}
li {
    display: inline-block;
    margin: 0 10px;
}
a {
    color: #42b983;
}

.demo-test-area {
    width: 300px;
    box-sizing: border-box;
    margin: auto;
}

.demo-test-area--text {
    box-sizing: border-box;
    width: 100%;
    margin: 0px;
    padding: 0px;
    resize: none;
    font-family: Avenir Next, Helvetica Neue, Helvetica,sans-serif;
    background: #fafbfc;
    color: #8da2b5;
    border: 1px solid #dde5ed;
    font-size: 16px;
    padding: 16px 15px 14px;
    margin: 0;
    border-radius: 6px;
    outline: none;
    height: 150px;
    margin-bottom: 10px;
}



.demo-test-area--preamble {
    padding: 20px 0px;
}

.demo-test-area--button {
    font-family: Avenir Next, Helvetica Neue, Helvetica,sans-serif;
    font-weight: 400;
    margin-top: 20px;
    user-select: none;
    border: none;
    line-height: 1.4;
    text-decoration: none;
    background: linear-gradient(45deg,#41b883,#34495d);
    color: white;
    padding: 6px 10px;
    font-size: 20px;
    height: 50px;
    border-radius: 4px;
    width: 80%;
    box-sizing: border-box;
    outline: none;
    cursor: pointer;
    align-self: center;
}

.demo-test-area--button:hover {
    background: linear-gradient(45deg,#34495d , #41b883);
}

.demo-test-area--wrapper {
    width: 100%;
    display: flex;
    flex-direction: column;
}


</style>
