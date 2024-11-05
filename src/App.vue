<template>
  <div id="app">
    <h1>Lista de Tarefas</h1>
    
    <!-- Input para adicionar nova tarefa -->
    <input v-model="novaTarefa" placeholder="Nova tarefa" @keyup.enter="adicionarTarefa" />
    <button @click="adicionarTarefa">Adicionar</button>

    <!-- Lista de tarefas -->
    <ul>
      <li v-for="(tarefa, index) in tarefas" :key="index">
        {{ tarefa }}
        <button @click="removerTarefa(index)">Remover</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      novaTarefa: "",
      tarefas: []
    };
  },
  methods: {
    adicionarTarefa() {
      if (this.novaTarefa.trim()) {
        this.tarefas.push(this.novaTarefa);
        this.novaTarefa = "";
      }
    },
    removerTarefa(index) {
      this.tarefas.splice(index, 1);
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  margin-top: 60px;
}
</style>
