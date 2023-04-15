<script setup>
import { ref } from 'vue'

const nome = ref('')
const email = ref('')
const senha = ref('')
const confirmaSenha = ref('')
const dataDeNascimento = ref()
const endereco = ref('')
const cidade = ref('')
const estado = ref()
const hobbies = ref('')
const hobbiesMostrar = ref([])
const lingProg = ref("")
const lingProgMostrar = ref([])
const biografia = ref('')

const mostrarInfo = ref(false)

function mostrar() {
  if (nome.value == "" || email.value == "" || senha.value == "" || dataDeNascimento.value == "" || endereco.value == "" || cidade.value == "" || estado.value == ("") || hobbiesMostrar.value == [] || lingProgMostrar.value == [] || biografia.value == "" || senha.value != confirmaSenha.value) {
    alert("Preencha todos os campos e verifique sua senha!")
    return false
  } else {
    return true
  }
}

function salvarLingProg() {
  lingProgMostrar.value.push(lingProg.value)
  lingProg.value = '';
}

function salvarHobbies() {
  hobbiesMostrar.value.push(hobbies.value)
  hobbies.value = '';
}


</script>

<template>
  <div class="container">
    <form v-if="!mostrarInfo" @submit.prevent="mostrarInfo = mostrar()">
      <h1>Formulario</h1>
      <input type="text" v-model="nome" placeholder="Digite seu nome" />
      <input type="email" v-model="email" placeholder="Digite seu email" />
      <input type="password" v-model="senha" placeholder="Digite sua senha" />
      <input type="password" v-model="confirmaSenha" placeholder="Confirme sua senha" />
      <input type="date" v-model="dataDeNascimento" placeholder="Insira sua data de nascimento" />
      <input type="text" v-model="endereco" placeholder="Insira seu endereco" />
      <input type="text" v-model="cidade" placeholder="Insira sua cidade" />
      <select v-model="estado" placeholder="Selecione seu estado">
        <option value="AC">Acre</option>
        <option value="AL">Alagoas</option>
        <option value="AP">Amapá</option>
        <option value="AM">Amazonas</option>
        <option value="BA">Bahia</option>
        <option value="CE">Ceará</option>
        <option value="DF">Distrido Federal</option>
        <option value="ES">Espírito Santo</option>
        <option value="GO">Goiania</option>
        <option value="MA">Maranhão</option>
        <option value="MT">Mato Grosso</option>
        <option value="MS">Mato Grosso do Sul</option>
        <option value="MG">Minas Gerais</option>
        <option value="PA">Pará</option>
        <option value="PB">Paraíba</option>
        <option value="PR">Paraná</option>
        <option value="PE">Pernambuco</option>
        <option value="PI">Piauí</option>
        <option value="RJ">Rio de Janeiro</option>
        <option value="RN">Rio Grande do Norte</option>
        <option value="RS">Rio Grande do Sul</option>
        <option value="RO">Rondônia</option>
        <option value="RR">Roraima</option>
        <option value="SC">Santa Catarina</option>
        <option value="SP">São Paulo</option>
        <option value="SE">Sergipe</option>
        <option value="TO">Tocantins</option>
      </select>
      <input class="inputsGrandes" type="text" v-model="hobbies" @keypress.enter="salvarHobbies()"
        placeholder="Digite seus hobbies favoritos (precione enter apos cada hobbie)" />
      <input class="inputsGrandes" type="text" v-model="lingProg" @keypress.enter="salvarLingProg()"
        placeholder="Digite as linguagens em que voce programa(precione enter apos cada hobbie)" />
      <label for="biografia">Biografia</label>
      <textarea v-model="biografia" rows="8"></textarea>
      <button type="submit">Enviar</button>
    </form>
    <div v-if="mostrarInfo" class="info">
      <h1>Suas informacoes</h1>
      <img src="/lindo.jpg" alt="">
        <div class="infos">
          <p>Nome: {{ nome }}</p>
          <p>Email: {{ email }}</p>
          <p>Senha: {{ senha }}</p>
          <p>Data De Nascimento: {{ dataDeNascimento }}</p>
          <p>Endereco: {{ endereco }}</p>
          <p>Cidade: {{ cidade }}</p>
          <p>Estado: {{ estado }}</p>
          <p>Hobbies: {{ hobbiesMostrar.join(", ") }}</p>
          <p>Linguagens que programa: {{ lingProgMostrar.join(", ") }}</p>
          <p>Biografia: {{ biografia }}</p>
        </div>
    </div>
  </div>
</template>

<style scoped>
img {
  width: 100px;
  border-radius: 4px;
  box-shadow: 2px 2px 0 1px rgba(0, 0, 0, 0.404);

}
h1{
  height: 50px;
}
p{
  padding-top: 12px;
}
.info {
  display: grid;
  grid-template-rows: 120px 100px ;
  width: 600px;
  height: 800px;
  background-color: rgb(255, 255, 255);
  border-radius: 5px;
  box-shadow: 7px 7px 0 3px rgba(0, 0, 0, 0.404);
  padding-left: 25px;
  
}
.infos p{
  font-weight: 600;
}

form {
  display: grid;
  grid-template-columns: 1fr;
  width: 600px;
  height: 800px;
  background-color: rgb(255, 255, 255);
  border-radius: 5px;
  box-shadow: 7px 7px 0 3px rgba(0, 0, 0, 0.404);
  padding-left: 25px;
}

select,
input {
  width: 250px;
  height: 30px;
  border: none;
  background-color: rgb(211, 211, 211);
  color: black;
  padding-left: 5px;
}

.inputsGrandes {
  width: 550px;
}

textarea {
  width: 250px;
  height: 40px;
  border-radius: 5px;
}

button {
  border: none;
  height: 40px;
  width: 250px;
  background-color: blueviolet;
  color: white;
  font-weight: 600;
  box-shadow: 2px 2px 0 1px rgba(0, 0, 0, 0.404);
  transition: 0.5s;
}

button:hover {
  border: none;
  height: 40px;
  width: 250px;
  background-color: rgb(255, 255, 255);
  color: blueviolet;
  font-weight: 600;
  box-shadow: 2px 2px 0 1px rgba(0, 0, 0, 0.404);
}
</style>
