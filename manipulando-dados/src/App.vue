<template>
  <div class="app" id="app">
    <div class="exercicio01">
      <p>{{total}}</p>

      <button @click="calcula('-')">-</button>
      <button @click="calcula('+')">+</button>
    </div>

    <div class="exercicio02">
      <p>Nome Computado: {{ nomeFormatado }}</p>
      <label>Input a computar</label>
      <input v-model="nome" type="text" />
    </div>

    <div class="exercicio03">
      <input v-model="busca" type="text" />
      <p v-text="resultado"></p>
    </div>
  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {
      total: 10,
      nome: "jose antonio",
      resultado: "",
      busca: ""
    };
  },

  watch: {
    busca: function(novoValor, valorAntigo) {
      this.resultado = "Aguardando o término da digitação...";
      this.recolheResposta();
    }
  },

  // nomeFormatado: {
  //   get: function() {
  //     console.log("executando computed")
  //     return this.nome.toLowerCase()
  //   },
  //   set: function(novoValor) {
  //     this.nome = novoValor.substring(0, 3)
  //   }
  // },

  computed: {
    nomeFormatado() {
      console.log("executando computed");
      return this.nome.toUpperCase();
    }
  },

  filters: {
    formataNome(valor) {
      valor = valor.toLowerCase();
      let corta = valor.split("");
      let resultado = "";
      for (let nome of corta)
        resultado += nome.charAt(0).toUpperCase() + nome.slice(1) + "";

      return resultado;
    }
  },

  methods: {
    calcula(sinal) {
      this.total = sinal == "-" ? this.total - 1 : this.total + 1;
    }
  },
  recolheResposta() {
    let valor = this.busca;
    setTimeout(() => {
      if (valor == this.busca) this.resultado = "Terminou de digitar";
    }, 500);
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

p {
  padding: 5px;
}

.class {
  text-align: center;
}

.exercicio01,
.exercicio02,
.exercicio03 {
  background-color: lightgrey;
  border: 15px solid green;
  padding: 50px;
  margin: 20px;
  align-items: center;
}
</style>
