<template>
  <div id="app">
  
    <fieldset>
    <CabecalhoApp msg="Painel dos Projetos"/>

    <div>
      <span>
        Tecnológica: <b>60% </b>
      </span>

      <span>
        Humanas: <b>30% </b>
      </span>

      <span>
        Médica: <b>10% </b>
      </span>
    </div>   

    </fieldset><br/><br/>

    <div class="menu">
      <button @click="showMenus.projectRegister = !showMenus.projectRegister">Cadastro de Projetos</button><br/><br/>
    </div>

    <hr>

    <div v-if="showMenus.projectRegister">
      <ProjectRegister />
      <hr>
    </div>

    <div>
      <br/>
      <a :href="url" target="_blank">Visualizar Projetos</a>
      <!-- {{ projects }} -->
    </div>
  </div>
</template>

<script>

import CabecalhoApp from './components/CabecalhoApp.vue'
import ProjectRegister from './components/projectRegister.vue'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    CabecalhoApp,
    ProjectRegister
  },
  data() {
    return {
      projects: [],
      showMenus: {
        projectRegister: false
      },
      url: 'https://projeto-prova.herokuapp.com/projeto'
    }
  },
  mounted() {
    axios
      .get('https://projeto-prova.herokuapp.com/projeto')
      .then(response => (this.projects = response))
  },
  solved(arr) {
    axios
      .post('https://projeto-prova.herokuapp.com/projeto', arr)
      .then(() => {
        this.mounted(this)
      })
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

b {
  font-size: 38px;
}

span {
  background-color: #F8F8FF;
  font-size: 14px;
}

button {
  color: #2c3e50;
  font-size: 18px;
  font-weight: bold;
  width: 77vh;
  height: 6vh;
}
</style>
