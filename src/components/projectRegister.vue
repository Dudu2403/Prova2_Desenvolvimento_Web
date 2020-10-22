<template>
    <div id="projectRegister">
        <form @submit.prevent="registerProject()" method="POST">            
            <div>
                <h1>Cadastro de Projetos</h1>
            </div>

            <div>
                <input type="text" placeholder="Informe o nome do projeto" v-model="newValues.nome">
            </div>

            <div>
                <select v-model="newValues.area">
                    <option disabled value="">Escolha uma área</option>
                    <option v-for="area in areasList" :key="area">{{ area }}</option>
                </select>
            </div>
            
            <div>
                <input type="number" placeholder="Informe o prazo (em dias)" v-model="newValues.prazo">
            </div>

            <div>
                <input type="number" min="5000" max="100000" placeholder="Informe o orçamento (Min: R$5000 Máx: R$100000)" v-model="newValues.orcamento">
            </div>

            <div>
                <button type="submit">Cadastrar</button><br/><br/>
            </div>  
        </form>
    </div>
</template>

<script src="https://cdn.jsdelivr.net/npm/vue@2.6"></script>

<script>

import App from '../App.vue'

export default {
  name: 'projectRegister',
  data() {
    return {
        newValues: {
            nome: '',
            area: '',
            prazo: '', 
            orcamento: null
        },
        areasList: ['TECNOLOGICA', 'HUMANA', 'MEDICA'],
    }
  },
  methods: {
    registerProject(){
        let project = JSON.parse(JSON.stringify(this.newValues))
        console.log(project)
        App.solved(this.newValues).then(answer => {
            alert(answer.id)
        })
    }
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
input {
    width: 76vh;
    height: 23px;
}
select {
    width: 77vh;
    height: 4vh;    
}

</style>
