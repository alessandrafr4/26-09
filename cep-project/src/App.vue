<script>
import axios from "axios";
export default {
  data() {
    return {
      cep: "",
      endereco: {},
    };
  },
  methods: {
    async buscar() {
      const url = `https://viacep.com.br/ws/${this.cep}/json/`;
      const res = await axios.get(url);
      this.endereco = res.data;
    },
  },
};
</script>

<template>
  <div class="position-absolute top-50 start-50 translate-middle w-50">
    <h1 class="">Buscar Cep</h1>
    <form class="row" @submit.prevent="buscar">
      <div class="col-9">
        <input
          class="form-control"
          type="text"
          v-model="cep"
          placeholder="Digite o CEP"
        />
      </div>
      <button class="btn btn-primary col-3" type="submit">Buscar</button>
    </form>
    <form class="end row">
      <div class="col-12">
        <label class="form-label" for="rua">Rua</label>
        <input class="form-control" type="text" v-model="endereco.logradouro" />
      </div>
      <div class="col-6">
        <label class="form-label" for="num">Número</label>
        <input class="form-control" type="text" v-model="endereco.numero" />
      </div>
      <div class="col-6">
        <label class="form-label" for="bairro">Bairro</label>
        <input class="form-control" type="text" v-model="endereco.bairro" />
      </div>
      <div class="col-6">
        <label class="form-label" for="complemento">Complemento</label>
        <input
          class="form-control"
          type="text"
          v-model="endereco.complemento"
        />
      </div>
      <div class="col-6">
        <label class="form-label" for="localidade">Localidade</label>
        <input class="form-control" type="text" v-model="endereco.localidade" />
      </div>
      <div class="col-6">
        <label class="form-label" for="uf">Estado</label>
        <input class="form-control" type="text" v-model="endereco.uf" />
      </div>
      <div class="col-6">
        <label class="form-label" for="ddd">DDD</label>
        <input class="form-control" type="text" v-model="endereco.ddd" />
      </div>
    </form>
  </div>
  {{ endereco }}
</template>
<style>
h1 {
  color: rgb(200, 140, 255);
}

.form button {
  color: rgb(0, 255, 221);
}

.position-absolute {
  background-color: rgb(183, 255, 255);
}
</style>
