<template>
  <div id="translateForm" class="row">
    <div class="col-md-12 col-md-offset-3">
      <form id="transform" class="well form-inline" v-on:submit="formSubmit">
        <input
          class="form-control"
          type="text"
          v-model="textToTranslate"
          placeholder="Ingrese una palabra"
        />
        <select class="form-control" v-model="language">
          <option value="ru">Ruso</option>
          <option value="en">Inglés</option>
          <option value="fr">Francés</option>
          <option value="zh">Chino</option>
          <option value="ko">Koreano</option>
          <option value="hi">Indio</option>
        </select>
        <input class="btn btn-primary" type="submit" value="Traducir" />
      </form>
      <br />
    </div>
  </div>
</template>

<script>
export default {
  name: "translateForm",
  data() {
    return {
      textToTranslate: "",
      language: ""
    };
  },
  created() {
    this.language = "ru";
  },
  methods: {
    formSubmit(e) {
      this.$emit("formSubmit", this.textToTranslate, this.language);
      e.preventDefault();
    }
  }
};
</script>

<style>
#transform {
  border-radius: 10px;
  border: 1px solid #ccc;
  padding: 2em 1em;
}
#transform > input {
  flex: 2;
}
#transform > select {
  flex: 1;
}
#transform > input[type="submit"] {
  flex: 1;
}
</style>
