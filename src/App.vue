<template>
  <div class="corpo">
    <h1 class="centralizar">{{ titulo }}</h1>

    <div>
    Filtre pelo título da foto: 
    <input type="search" class="filtro" v-on:input="filtro=$event.target.value" placeholder="escreva o título">
    </div>

    <ul class="listarfotos">
      <li class="listafotositem" v-for="foto of fotosComFiltro">
        <meu-painel :titulo="foto.titulo">
          <imagem-responsiva v-bind:src="foto.url" v-bind:alt="foto.titulo"/>
        </meu-painel>
      </li>
    </ul>
  </div>
</template>

<script>
import Painel from "./components/shared/painel/Painel.vue";
import ImagemResponsiva from './components/shared/imagem-responsiva/ImagemResponsiva.vue'

export default {
  components: {
    "meu-painel": Painel,
    'imagem-responsiva': ImagemResponsiva

  },

  data() {
    return {
      titulo: "Alurapic",
      fotos: [],
      filtro: ''
    };
  },

  computed: {
    fotosComFiltro() {
      if (this.filtro) {
        let exp = new RegExp(this.filtro.trim(), "i");
        return this.fotos.filter(foto => exp.test(foto.titulo));
      } else {
        return this.fotos;
      }
    }
  },

  created() {
    this.$http
      .get("http://localhost:3000/v1/fotos")
      .then(res => res.json())
      .then(fotos => (this.fotos = fotos), err => console.log(err));
  }
};
</script>

<style>
.corpo {
  font-family: "Franklin Gothic Medium", "Arial Narrow", Arial, sans-serif;
  width: 96%;
  margin: 0 auto;
}

.centralizar {
  text-align: center;
}

.listarfotos {
  list-style: none;
}

.listafotositem {
  display: inline-block;
}

.imagem-responsiva {
  width: 100%;
}

.filtro{
  display: block;
  width:100%;
}
</style>
