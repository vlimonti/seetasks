<template>
  <header>
      <h1>
        <img src="../assets/logo.png" alt="See Tasks">  
      </h1>
      <button class="button small-btn default-btn" @click="alterarTema">
        {{ textoBotao }}
      </button>
  </header>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'BarraLateral',
  emits: ['aoTemaAlterado'],
  data () {
    return {
      modoEscuroAtivo: false
    }
  },
  computed: {
    textoBotao () {
      if (this.modoEscuroAtivo) {
        return 'Modo claro'
      }
      return 'Modo escuro'
    }
  },
  methods: {
    alterarTema () {
      this.modoEscuroAtivo = !this.modoEscuroAtivo
      this.$emit('aoTemaAlterado', this.modoEscuroAtivo)
    }
  }
})
</script>

<style scoped>
header {
  padding: 1rem;
  background: #0a2034;
  width: 100%;
  height: 100vh;
  text-align: center;
}
@media only screen and (max-width: 768px) {
  header {
    padding: 2.5rem;
    height: auto;
  }
}

.default-btn {
  margin:15px;
  background-color: #89d2ff;
  color: #141414;
  padding: 10px;
  border-radius: 5px;
  -moz-border-radius: 10px;
  -webkit-border-radius: 10px;
}

.small-btn {
        width: 125px;
        height: 25px;
    }
</style>
