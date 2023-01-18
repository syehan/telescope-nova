<template>
  <div>
    <Head :title="pageTitle" />
    <Card
      class="flex flex-col items-center justify-center"
      style="min-height: 300px"
    >
    <iframe
        :src="this.telescope_url"
        class="w-full aspect-auto"
        frameborder="0"
        scrolling="auto"
    ></iframe>
    </Card>
  </div>
</template>

<script>
export default {
  props: {
    pageTitle: {
      type: String,
      required: false,
      default: 'Telescope Nova',
    },
  },

  data() { 
    return {
      telescope_url: "",
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

<style>
iframe {
      height: 80vh;
      transform: scale(1);
      -webkit-transform:scale(1);
      -moz-transform:scale(1);
  }
</style>
