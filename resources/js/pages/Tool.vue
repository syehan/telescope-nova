<template>
  <Head title="Telescope Nova" />
  <iframe
      :src="this.telescope_url"
      class="w-full aspect-auto"
      frameborder="0"
      scrolling="auto"
  ></iframe>
</template>

<script>
export default {
  data() { 
    return {
      telescope_url: null,
    }
  },
  async mounted() {
    await this.getPath();
  },
  methods: {
    getPath() {
      Nova.request().get("/nova-vendor/syehan/telescope/telescope-url")
        .then((response) => {
        this.telescope_url = ("/" + response.data).replace("\/\/", "\/");
      });
    }
  }
}
</script>

<style scoped>
iframe {
    height: 80vh;
    -webkit-transform:scale(1);
    -moz-transform:scale(1);
}
</style>