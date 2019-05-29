<template>
  <div class="corpo">
    <h1 class="centralizar">{{ titulo }}</h1>
    <ul class="listarfotos">
      <li class="listafotositem" v-for="foto of fotos">
       
        <div class="painel">
          <h2 class="painel-titulo">{{foto.titulo}}</h2>
          <div class="painel-corpo">
            <img class="imagem-responsiva" v-bind:src="foto.url" v-bind:alt="foto.titulo">
          </div>
        </div>
      
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      titulo: "Alurapic",
      fotos: []
    };
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

.imagem-responsiva{
  width: 100%;
}

/* estilo do painel */ 

   .painel {
    padding: 0 auto;
    border: solid 2px peru;
    display: inline-block;
    margin: 5px;
    box-shadow: 5px 5px 10px grey;
    width: 200px;
    height: 100%;
    vertical-align: top;
    text-align: center;
  }

  .painel .painel-titulo {
    text-align: center;
    border: solid 2px;
    background: purple;
    margin: 0 0 15px 0;
    padding: 10px;
    text-transform: uppercase;
    color: blanchedalmond;  
    }

</style>
