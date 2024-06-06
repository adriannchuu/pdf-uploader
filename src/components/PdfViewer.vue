<template>
    <div>
      <canvas ref="pdfCanvas"></canvas>
    </div>
  </template>
  
  <script>
  import * as pdfjsLib from "pdfjs-dist/webpack";
  import "pdfjs-dist/web/pdf_viewer.css";
  
  export default {
    props: {
      pdfData: ArrayBuffer
    },
    watch: {
      pdfData: "renderPdf"
    },
    methods: {
      async renderPdf() {
        const pdf = await pdfjsLib.getDocument(this.pdfData).promise;
        const page = await pdf.getPage(1);
        const viewport = page.getViewport({ scale: 1.5 });
        const canvas = this.$refs.pdfCanvas;
        const context = canvas.getContext("2d");
        canvas.height = viewport.height;
        canvas.width = viewport.width;
        page.render({ canvasContext: context, viewport: viewport });
      }
    }
  };
  </script>