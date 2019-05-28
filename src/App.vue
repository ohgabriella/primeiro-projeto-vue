<template>
  <div class="corpo">
    <h1 class = "centralizar">{{ titulo }}</h1>
    <ul class= "listarfotos">
      <li class = "listafotositem" v-for="foto of fotos">
       <img v-bind:src="foto.url" v-bind:alt="foto.titulo">
      </li>

    </ul>
  </div>
</template>

<script>
export default {
  data(){
    return{
      titulo: 'Alurapic',
      fotos: []
    }
  },
  created(){
    this.$http.get('http://localhost:3000/v1/fotos')
      .then( res =>  res.json())
      .then(fotos => this.fotos = fotos, err => console.log(err));
    }
}
</script>

<style>
.corpo{
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  width: 96%;
  margin: 0 auto;
}

.centralizar{
  text-align: center;
}

.listarfotos{
  list-style: none;
}

.listafotositem{
  display: inline-block;
}

</style>
