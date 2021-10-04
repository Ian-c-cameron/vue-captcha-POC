<template>
  <div id="app">
    <Recaptcha v-if="!isRecaptchaValid"
                    :apiBasePath="recaptchaAPIBasePath"
                    :nonce="applicationUuid"
                    :publicKey="this.recaptchaPublicKey"
                    @recaptchaVerified="handleCaptchaVerified($event)" />
  </div>
</template>

<script>
import {Recaptcha} from 'common-lib-vue';

export default {
  name: 'App',
  components: {
    Recaptcha,
  },
  data: () => {
    return {
      recaptchaPublicKey: "6LfHcJcbAAAAAJA_kkeR4AXt92hSUpCxb-mKeWkT",
      recaptchaAPIBasePath: "https://recaptcha-service-e1aae2-dev.apps.silver.devops.gov.bc.ca",
      applicationUuid: "Testing",
      isRecaptchaValid: false,
    }
  },
  methods:  {
    // getFocusableEls() {
    //   // Create an array of focusable elements from the contents of the modal
    //   return Array.from(this.$refs.modal.querySelectorAll('a[href], area[href], input:not([disabled]), select:not([disabled]), textarea:not([disabled]), button, [tabindex="0"]'));
    // },
    handleCaptchaVerified(captchaToken) {
      console.log("Verified", captchaToken);
      // this.$store.dispatch(formModule + '/' + SET_CAPTCHA_TOKEN, captchaToken);
      this.isRecaptchaValid = true;
      // setTimeout(() => {
      //   this.focusableEls = this.getFocusableEls();
      // }, 0);
    },
  },
}
</script>

<style></style>
