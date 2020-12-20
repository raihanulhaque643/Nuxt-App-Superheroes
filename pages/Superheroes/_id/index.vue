<template>
  <div class='container'>

      <img :src=images.lg alt=''>

      <div class='row'>Full Name: <span class='right'>{{biography.fullName}}</span></div>
      <div class='row'>Place of Birth: <span class='right'>{{biography.placeOfBirth}}</span></div>
      <div class='row'>First Appearance: <span class='right'>{{biography.firstAppearance}}</span></div>
      <div class='row'>Alter Ego: <span class='right'>{{biography.alterEgos}}</span></div>
      <div class='row'>Publisher:<span class='right'>{{biography.publisher}}</span></div>

      <div class='row'>Eye color: <span class='right'>{{appearance.eyeColor}}</span></div>
      <div class='row'>Gender: <span class='right'>{{appearance.gender}}</span></div>
      <div class='row'>Hair color: <span class='right'>{{appearance.hairColor}}</span></div>
      <div class='row'>Height: <span class='right'>{{appearance.height}}</span></div>
      <div class='row'>Race: <span class='right'>{{appearance.race}}</span></div>
      <div class='row'>Weight: <span class='right'>{{appearance.weight}}</span></div>

      <div class='row'>Combat: <span class='right'>{{powerstats.combat}}</span></div>
      <div class='row'>Durability: <span class='right'>{{powerstats.durability}}</span></div>
      <div class='row'>Intelligence: <span class='right'>{{powerstats.intelligence}}</span></div>
      <div class='row'>Power: <span class='right'>{{powerstats.power}}</span></div>
      <div class='row'>Speed: <span class='right'>{{powerstats.speed}}</span></div>
      <div class='row'>Strength: <span class='right'>{{powerstats.strength}}</span></div>

  </div>
</template>

<script>
import axios from 'axios';

export default {
  data(){
    return {
      name: {},
      biography: {},
      appearance: {},
      powerstats: {},
      images: {}
    }
  },
  async created() {
        const config = {
            headers: {
                Accept: "application/json"
            }
        }

        try {
           const res = await axios.get(`https://cdn.jsdelivr.net/gh/akabab/superhero-api@0.3.0/api/id/${this.$route.params.id}.json`, config);
           
          this.name = res.data.name;
           this.biography = res.data.biography;
           this.appearance = res.data.appearance;
           this.powerstats = res.data.powerstats;
           this.images = res.data.images;
          //  console.log(this.superhero);
        } catch (err) {
            console.error(err);
        }

    },

    head() {
        return {
            title: this.name,
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
  .row {
    background: rgb(2, 2, 99);
    color: white;
    margin: 10px;
    padding: 10px;
    border-radius: 15px;
  }
  .right {
    float: right;
  }
</style>