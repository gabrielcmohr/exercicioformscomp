<script setup>
import { ref, defineProps } from 'vue'

const titulo = ref('Seus dados aqui')

const props = defineProps({
  usuario: {
    type: Object
  }
})
</script>

<template>
  <div class="container-dados">
    <h1>{{ titulo }}</h1>
    <p>Nome: {{ props.usuario.nome }}</p>
    <p>Email: {{ props.usuario.email }}</p>
    <p>Senha: {{ props.usuario.senha }}</p>
    <p>Endereço: {{ props.usuario.endereco }}</p>
    <p>Cidade: {{ props.usuario.cidade }}</p>
    <p>Estado: {{ props.usuario.estadoSelecionado }}</p>
    <p>Data de Nascimento: {{ props.usuario.dataNascimento }}</p>
    <p>Hobbies: {{ props.usuario.hobbies }}</p>
    <p>Linguagens de Programação: {{ props.usuario.linguagensProgramacao }}</p>
    <p>Biografia: {{ props.usuario.biografia }}</p>
  </div>
</template>

<style scoped>
.container-dados {
  background-color: #f4f4f4;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 20px; 
  border-radius: 8px; 
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  max-width: 800px;
  margin: 20px auto;
}

@media (max-width: 768px) {
  .container-dados {
    padding: 15px;
  }
}
</style>
