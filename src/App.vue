<template>
  <header>
    <div class="wrapper">
      <HelloWorld msg="PDF Viewer" />
    </div>
  </header>
  <main>
    <div id="app">
      <PdfUploader @file-loaded="handleFileLoaded" />
      <PdfViewer v-if="pdfData" :pdfData="pdfData" />
    </div>
  </main>
  
</template>

<script>
import PdfUploader from "./components/PdfUploader.vue";
import PdfViewer from "./components/PdfViewer.vue";


export default {
  components: {
    PdfUploader,
    PdfViewer
  },
  data() {
    return {
      pdfData: null
    };
  },
  methods: {
    handleFileLoaded(data) {
      this.pdfData = data;
    }
  }
};
</script>

<style>
#app {
  text-align: center;
  margin-top: 50px;
}
</style>
<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
