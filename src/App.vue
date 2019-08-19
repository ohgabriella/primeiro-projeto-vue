<template>
  <div class="corpo">

   <nav>      
   <ul>        
   <li> <router-link to="/">HOME</router-link>        
   </li>        
   <li> <router-link to="/cadastro">CADASTRO</router-link>        
   </li>      
   </ul>    
   </nav>    
   <router-view>    
   </router-view>

  </div>
</template>

<script>

</script>

<style>
.corpo {
  font-family: "Franklin Gothic Medium", "Arial Narrow", Arial, sans-serif;
  width: 96%;
  margin: 0 auto;
}

</style>
