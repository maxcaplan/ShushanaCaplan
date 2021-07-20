<template>
  <div id="home"></div>
</template>

<script>
export default {
  name: "home",

  head() {
    return {
      script: [
        { src: "https://identity.netlify.com/v1/netlify-identity-widget.js" }
      ]
    };
  }
};
</script>
