<template>
  <div>
    <h1>{{ titulo }}</h1>
    <img v-bind:src="foto[0].url" v-bind:alt="foto[0].titulo">
    <img src="https://levesemdestino.com/wp-content/uploads/2018/09/bolivia-o-que-saber-antes-de-ir-mochilao-chile-bolivia-peru-america-do-sul-uyuni-atacama.jpg" alt="Bolívia">

  </div>
</template>

<script>
export default {
  data(){
    return{
      titulo: 'Alurapic',
      foto: [
        {
        url: 'https://media.istockphoto.com/photos/presidential-palace-in-asuncion-paraguay-picture-id525336822?k=6&m=525336822&s=612x612&w=0&h=M_EjzCwczCG5DbJHT83ZNStFa0sfLZmPv8uELCUU7wc=',
        titulo: 'Paraguay'
        }
                
        ]
    }

  }
  
}
</script>

<style>

</style>
