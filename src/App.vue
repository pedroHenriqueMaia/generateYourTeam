<template>
  <div class="app">
    <h2 style="color: white" class="mt-5" align="center">{{ title }}</h2>
    <div class="row">
      <Character 
        v-for="(id, index) in initial_ids"
        :id="id"
        key="index"
      />
    </div>
  </div>
</template>

<script>
  import Character from './components/Character.vue'; 

  export default {
    nme: 'app',
    data() {
      return {
        title: 'Generate Your Team',
        initial_ids: [1, 2, 3]
      }
    },
    components: {
      Character
    } 
  }
</script>