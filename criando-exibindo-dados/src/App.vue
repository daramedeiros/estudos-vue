<template>
  <div id="app">
    <h1 v-once v-text="titulo"></h1>

    <input v-bind:disabled="tarefas.length == 0" v-model="subtitulo" type="text" />

    <div v-if="tarefas.length <= 0">Não há tarefas</div>
    <div v-if="tarefas.length > 0">
      Existem {{tarefas.length}} tarefas
      <ul>
        <li v-for="tarefa in tarefas" :key="tarefa.id">{{tarefa}}</li>
      </ul>
    </div>
    <button @click="tarefas = []">Limpar</button>
  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {
      msg: "Welcome to Your Vue.js App"
    };
  },
  name: "lv-tarefas",
  data() {
    return {
      titulo: "Listagem de tarefas",
      subtitulo: "Defina uma descrição",
      tarefas: []
    };
  },
  mounted() {
    setTimeout(() => {
      this.titulo = "novo título";
      this.tarefas = ["tarefa 1", "tarefa 2", "tarefa 3", "tarefa 4"];
    }, 3000);
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1,
h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
