<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <Recaptcha v-if="!isRecaptchaValid"
                    :apiBasePath="recaptchaAPIBasePath"
                    :nonce="applicationUuid"
                    :publicKey="this.recaptchaPublicKey"
                    @recaptchaVerified="handleCaptchaVerified($event)" />
  </div>
</template>

<script>
import { Recaptcha } from 'common-lib-vue';

export default {
  name: 'App',
  components: {
    Recaptcha
  },
  data: () => {
    return {
      recaptchaPublicKey: "6LfHcJcbAAAAAJA_kkeR4AXt92hSUpCxb-mKeWkT",
    }
  },
  methods:  {
    getFocusableEls() {
      // Create an array of focusable elements from the contents of the modal
      return Array.from(this.$refs.modal.querySelectorAll('a[href], area[href], input:not([disabled]), select:not([disabled]), textarea:not([disabled]), button, [tabindex="0"]'));
    },
    handleCaptchaVerified(captchaToken) {
      console.log("Verified", captchaToken);
      // this.$store.dispatch(formModule + '/' + SET_CAPTCHA_TOKEN, captchaToken);
      // this.isCaptchaValid = true;
      // setTimeout(() => {
      //   this.focusableEls = this.getFocusableEls();
      // }, 0);
    },
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
