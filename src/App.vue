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
const lingProg = ref([])
const biografia = ref('')

const mostrarInfo = ref(false)

function mostrar() {
  if (senha.value == confirmaSenha.value) {
    return true
  } else {
    return false
  }
}
</script>

<template>
  <div class="container">
    <div class="formulario">
      <form @submit.prevent="mostrarInfo = mostrar()">
        <label for="nome">Digite seu nome: </label>
        <input type="text" v-model="nome" placeholder="Digite seu nome" required />
        <label for="email">Digite seu email: </label>
        <input type="email" v-model="email" placeholder="Digite seu email" required />
        <label for="senha">Digite sua senha: </label>
        <input type="password" v-model="senha" placeholder="Digite sua senha" required />
        <label for="confirmarSenha">Confirme sua senha: </label>
        <input type="password" v-model="confirmaSenha" placeholder="Confirme sua senha" required />
        <label for="dataDeNascimento">Data de Nascimento: </label>
        <input type="date" v-model="dataDeNascimento" />
        <label for="endereco">Digite seu Endereco: </label>
        <input type="text" v-model="endereco" required />
        <label for="cidade">Digite seu Cidade </label>
        <input type="text" v-model="cidade" required />
        <label for="estado">Digite seu Estado: </label>
        <select v-model="estado">
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
        <label for="hobbies">Selecione seu hobbie favorito: </label>
        <select v-model="hobbies">
          <option value="computação">computação</option>
          <option value="esporte">esporte</option>
          <option value="musica">musica</option>
        </select>
        <label for="lingProg">Selecione as linguagens em que você programa: </label>
        <input type="text" v-model="lingProg" required />
        <label for="biografia">Biografia</label>
        <textarea v-model="biografia" rows="8"></textarea>
        <button type="submit">Enviar</button>
      </form>
    </div>
    <div v-if="mostrarInfo" class="info">
      <p>nome: {{ nome }}</p>
      <p>email: {{ email }}</p>
      <p>senha: {{ senha }}</p>
      <p>confirmaSenha: {{ confirmaSenha }}</p>
      <p>dataDeNascimento: {{ dataDeNascimento }}</p>
      <p>endereco: {{ endereco }}</p>
      <p>cidade: {{ cidade }}</p>
      <p>estado: {{ estado }}</p>
      <p>hobbies: {{ hobbies }}</p>
      <p>lingProg: {{ lingProg }}</p>
      <p>biografia: {{ biografia }}</p>
    </div>
  </div>
</template>

<style scoped>

.formulario {
  width: 300px;
  height: 800px;
  background-color: blueviolet;
}
.info {
  display: grid;
  grid-template-columns: 1fr;
  width: 300px;
  height: 800px;
  background-color: blueviolet;
}

form {
  display: grid;
  grid-template-rows: 1fr 1fr;
}

select,
input {
  width: 250px;
  height: 25px;
  border-radius: 8px;
}

textarea {
  width: 250px;
  border-radius: 8px;
}
</style>
