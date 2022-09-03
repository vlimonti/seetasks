<template>
  <header>
      <h1>
        <img src="../assets/logo.png" alt="See Tasks">  
      </h1>
      <div>
        <button class="button small-btn default-btn" @click="alterarTema">
          {{ textoBotao }}
        </button>
      </div>
      <nav class="panel mt-5">
        <ul>
          <li>
            <router-link to="/" class="link">
              <i class="fas fa-tasks"></i>
              Tarefas
            </router-link>
          </li>
          <li>
            <router-link to="/projetos" class="link">
              <i class="fas fa-project-diagram"></i>
              Projetos
            </router-link>
          </li>
        </ul>
      </nav>
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
    background-color: #dae5eb;
    color: #141414;
    padding: 10px;
    border-radius: 5px;
    -moz-border-radius: 10px;
    -webkit-border-radius: 10px;
  }

  .default-btn:hover {
    background-color: #96bed5;
  }

  .small-btn {
          width: 125px;
          height: 25px;
  }

  .panel li {
      margin: 8px 0;
  }

  .link {
      color: #fff;
  }

  .link:hover {
      color: #bbd6ff;
  }

  .link.router-link-active {
      color: #bbd6ff;
  }

</style>
