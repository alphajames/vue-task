<template>
  <!-- TASK CONTAINER -->
<div class=" col-xl-6 container-padding ">
<ul>
  <li v-for="todo in todos" :key="todo.id">
    <h1 class="font-poppins text-2xl pb-5 task-container"> {{todo.content}}  <button class="ms-3 delete"><i class="far fa-trash-alt font-white"></i></button></h1>
    
  </li>
</ul>
</div>
<!-- END TASK CONTAINER -->
</template>

<script>

export default {

}
</script>

<style>

</style>