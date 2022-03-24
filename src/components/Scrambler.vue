<template>
  <div class="scrambler">
    <div class="container">
      <textarea
        class="textarea"
        placeholder="Text something"
        v-model="message"
      >
      </textarea>
      <button 
        class="button" 
        :class="[message ? 'button--on' : '']"
        v-on:click="toggle"
      >{{ isActive  ? 'Hide Secret' : 'Show Secret'}}</button>
      <textarea
        class="textarea"
        v-model="scramblerMessage"
        v-if="showMessage"
        readonly
      >
      </textarea>
    </div>
  </div>
</template>

<script>
  export default {
    name: "ScramblerText",
    data() {
      return {
        message: '',
        isActive: false,
        showHideText: false,
        showMessage: false,
      }
    },
    computed: {
      scramblerMessage: function () {
        return this.message.split('').sort(() => Math.random() - 0.5).join('');
      }
    },
    methods: {
      toggle: function () {
        if ( this.message != '' ) {
          this.isActive = this.isActive ? false : true;
          this.showHideText = this.showHideText ? false : true;
          this.showMessage = this.showMessage ? false : true;
        }
      }
    }
  };
</script>

<style>
  body {
    background: #cca9dd;
  }
  
  h1 {
    color: #fff;
  }

  .container {
    display: flex;
    flex-direction: column;
    margin: 0 auto;
    max-width: 500px;
  }

  .textarea {
    border-radius: 5px;
    border: none;
    height: 60px;
    margin-bottom: 20px;
    padding: 10px;
  }

  .button {
    background: #f6f6f6;
    border-radius: 2px;
    border: none;
    cursor: not-allowed;
    margin: 0 auto 20px;
    max-width: 200px;
    padding: 10px;
  }

  .button--on {
    background: #28a745;
    color: #fff;
    cursor: pointer;
  }
</style>