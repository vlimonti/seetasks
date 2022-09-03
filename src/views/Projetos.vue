<template>
    <section class="projetos">
        <form @submit.prevent="salvar">
            <div class="columns">
                <div class="column is-9" role="form">
                    <input 
                        type="text" 
                        class="input" 
                        placeholder="Digite o nome do projeto..."
                        v-model="nomeDoProjeto" 
                        id="nomeDoProjeto"
                    />
                </div>
                <div class="column is-3">
                    <button class="button" type="submit">
                        Salvar
                    </button>
                </div>
            </div>
        </form>
        <div><br></div>
        <table class="table is-fullwidth is-striped is-hoverable">
            <thead>
                <tr>
                    <th>ID</th>
                    <th>Nome</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="projeto in projetos" :key="projeto.id">
                    <td>{{ projeto.id }}</td>
                    <td>{{ projeto.nome }}</td>
                </tr>
            </tbody>
        </table>
    </section>
</template>

<script lang="ts">
import { computed, defineComponent } from 'vue';
import { useStore } from "@/store"

export default defineComponent({
    name: "Projetos",
    data () {
        return { 
            nomeDoProjeto: ""
        };
    },
    methods: {
        salvar () {
            this.store.commit('ADICIONA_PROJETO', this.nomeDoProjeto)
            this.nomeDoProjeto = ''
        },
    },
    setup () {
        const store = useStore()
        return {
            store,
            projetos: computed(() => store.state.projetos )
        }
    }
});
</script>

<style scoped>
.projetos {
    padding: 1.25rem;
}
</style> 