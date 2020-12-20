<template>
<nuxt-link :to="'superheroes/' + superhero.id">
  <div class='superhero'>
      <img :src=superhero.images.sm alt=''>
      <div class='superheroInfo'>
          <div><span class='bold'>Name: </span>{{superhero.name}}</div>
          <div><span class='bold'>Relatives: </span>{{superhero.connections.relatives}}</div>
          <div><span class='bold'>Group Affiliation: </span>{{superhero.connections.groupAffiliation}}</div>
        </div>
  </div>
</nuxt-link>
</template>

<script>
export default {
    name: 'Superhero',
    props: ['superhero']

}
</script>

<style>
*{
    box-sizing: border-box;
}
    .superhero {
        padding: 1rem;
        border: 1px dotted #ccc;
        margin: 1rem 0;
        display: flex;
    }
    .superhero img {
        object-fit: contain;
    }
    .superheroInfo {
        margin-left: 4px;
        margin-right: 0px;
        padding: 0px 10px;
        height: auto;
        width: 100%;
        background: rgb(6, 65, 85);
        color: white;
    }
    .bold {
        font-weight: bold;
    }
</style>