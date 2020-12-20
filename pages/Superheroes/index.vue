<template>
  <div class=''>
      <Superhero v-for="superhero in superheroes"
      :key="superhero.id" 
      :superhero="superhero"
       />
  </div>
</template>

<script>
import axios from 'axios';
import Superhero from '../../components/Superhero.vue';

export default {
    components: {
        Superhero
    },
    data() {
        return {
            superheroes: []
        }
    },
    async created() {
        const config = {
            headers: {
                Accept: "application/json"
            }
        }

        try {
           const res = await axios.get('https://cdn.jsdelivr.net/gh/akabab/superhero-api@0.3.0/api/all.json', config);
           console.log(res.data);

           this.superheroes = res.data
        } catch (err) {
            console.error(err);
        }

    },
    head() {
        return {
            title: 'Superheroes',
            meta: [
                {
                    hid: 'description',
                    name: 'description',
                    content: 'Best place for superheroes'
                }
            ]
        }
    }
}
</script>

<style>

</style>