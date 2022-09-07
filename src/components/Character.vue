<template>
    <div class="col-4" @click="switchCharacter">
      <div class="card" align="center">
        <img class="card-img-top" v-bind:src='character.image' v-bind:alt='character.name'>
        <div class="card-body">
          <h5 class="card-title">{{ character.name }} <small class="text-secondary">({{ character.gender }})</small></h5>
          <p class="card-text">{{ character.species }}</p>
        </div>
        <ul class="list-group list-group-flush">
          <li class="list-group-item">{{ character.location.name }}</li>
          <li class="list-group-item">{{ character.origin.name }}</li>
        </ul>
      </div>
    </div>
</template>

<script>
  export default {
    props: ['id'],
    data() {
      return {
        character: {}
      }
    },
    methods: {
      fetchCharacter(id) {
        fetch(`https://rickandmortyapi.com/api/character/${id}`, {
          method: 'GET'
        })
        .then(response => response.json())
        .then(character => this.character = character)
      },
      switchCharacter() {
        let random_id = Math.floor(Math.random() * 83 + 1)
        this.fetchCharacter(random_id)
      }
    },
    created() {
      this.fetchCharacter(this.id)
    }
  }
</script>