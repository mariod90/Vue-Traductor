<template>
  <div id="app" class="container text-center">
    <h1>Traductor de palabras</h1>
    <h5>Desarrollado en Vue.js</h5>
    <br>
    <TranslateForm v-on:formSubmit="translateText"></TranslateForm>
    <TranslateOutput v-text="translatedText"></TranslateOutput>
  </div>
</template>

<script>
import TranslateForm from "./components/TranslateForm";
import TranslateOutput from "./components/TranslateOutput";

export default {
  name: "App",
  components: {
    TranslateForm,
    TranslateOutput
  },
  data: function() {
    return {
      translatedText: ""
    };
  },
  methods: {
    translateText: function(text, language) {
      this.$http
        .get(
          "https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20190929T194906Z.0de7dd29590cf591.b85cca843573a115a1a66b989217b19408fc281a" +
            "&lang=" +
            language +
            "&text=" +
            text
        )
        .then(response => {
          this.translatedText = response.body.text[0];
        });
    }
  }
};
</script>

<style>
body{
  background-color: #f3f3f3;
}
</style>
