<script setup>
import { reactive, ref, computed, defineEmits, defineProps } from 'vue'

defineProps(['titulo'])

const emit = defineEmits(['formularioEnviado'])

const usuario = reactive({
  nome: '',
  email: '',
  senha: '',
  confirmarSenha: '',
  endereco: '',
  cidade: '',
  estadoSelecionado: '',
  dataNascimento: '',
  hobbies: '',
  linguagensProgramacao: '',
  biografia: ''
})

const mostrarDados = ref(false)
const textoBotao = computed(() => (mostrarDados.value ? 'Ocultar' : 'Mostrar'))

const estados = [
  { uf: 'AC', nome: 'Acre' },
  { uf: 'AL', nome: 'Alagoas' },
  { uf: 'AP', nome: 'Amapá' },
  { uf: 'AM', nome: 'Amazonas' },
  { uf: 'BA', nome: 'Bahia' },
  { uf: 'CE', nome: 'Ceará' },
  { uf: 'DF', nome: 'Distrito Federal' },
  { uf: 'ES', nome: 'Espírito Santo' },
  { uf: 'GO', nome: 'Goiás' },
  { uf: 'MA', nome: 'Maranhão' },
  { uf: 'MT', nome: 'Mato Grosso' },
  { uf: 'MS', nome: 'Mato Grosso do Sul' },
  { uf: 'MG', nome: 'Minas Gerais' },
  { uf: 'PA', nome: 'Pará' },
  { uf: 'PB', nome: 'Paraíba' },
  { uf: 'PR', nome: 'Paraná' },
  { uf: 'PE', nome: 'Pernambuco' },
  { uf: 'PI', nome: 'Piauí' },
  { uf: 'RJ', nome: 'Rio de Janeiro' },
  { uf: 'RN', nome: 'Rio Grande do Norte' },
  { uf: 'RS', nome: 'Rio Grande do Sul' },
  { uf: 'RO', nome: 'Rondônia' },
  { uf: 'RR', nome: 'Roraima' },
  { uf: 'SC', nome: 'Santa Catarina' },
  { uf: 'SP', nome: 'São Paulo' },
  { uf: 'SE', nome: 'Sergipe' },
  { uf: 'TO', nome: 'Tocantins' }
]

function verificarDados() {
  if (usuario.nome === '') {
    alert('"Nome" é obrigatório')
    Event.preventDefault() 
  } else if (usuario.email === '') {
    alert('"Email" é obrigatório')
    Event.preventDefault()
  } else if (usuario.senha === '') {
    alert('"Senha" é obrigatória')
    Event.preventDefault()
  } else if (usuario.confirmarSenha === '') {
    alert('"Confirmar senha" é obrigatório')
    Event.preventDefault()
  } else if (usuario.endereco === '') {
    alert('"Endereço" é obrigatório')
    Event.preventDefault()
  } else if (usuario.estadoSelecionado === '') {
    alert('"Estado" é obrigatório')
    Event.preventDefault()
  } else if (usuario.dataNascimento === '') {
    alert('"Data de nascimento" é obrigatória')
    Event.preventDefault()
  } else if (usuario.cidade === '') {
    alert('"Cidade" é obrigatória')
    Event.preventDefault()
  } else if (usuario.hobbies === '') {
    alert('"Hobbies" são obrigatórios')
    Event.preventDefault()
  } else if (usuario.linguagensProgramacao === '') {
    alert('"Linguagens de programação" são obrigatórias')
    Event.preventDefault()
  } else if (usuario.biografia === '') {
    alert('"Biografia" é obrigatória')
    Event.preventDefault()
  } else if (usuario.senha !== usuario.confirmarSenha) {
    alert('As senhas devem ser iguais.')
    Event.preventDefault()
  } else {
    mostrarDados.value = !mostrarDados.value
    emit('formularioEnviado', { ...usuario })
  }
}
</script>

<template>
  <div class="container-formulario">
    <div class="container-titulo">
      <h1 class="titulo" id="titulo-estatico">Forms</h1>
      <h1 class="titulo" id="titulo-dinamico">{{ titulo }}</h1>
    </div>
    <form action="" class="formulario" @submit.prevent="verificarDados()">
      <div class="layout-2-2">

        <div class="item-formulario">
          <label for="nome">Nome:</label>
          <input type="text" name="nome" id="nome" v-model="usuario.nome" />
        </div>

        <div class="item-formulario" id="area-email">
          <label for="email">Email:</label>
          <input type="email" name="email" id="email" v-model="usuario.email" />
        </div>

        <div class="item-formulario">
          <label for="senha">Senha:</label>
          <input type="password" name="senha" id="senha" v-model="usuario.senha" />
        </div>

        <div class="item-formulario" id="area-confirmar-senha">
          <label for="confirmar-senha">Confirme sua senha:</label>
          <input
            type="password"
            name="confirmarSenha"
            id="confirmar-senha"
            v-model="usuario.confirmarSenha"
          />
        </div>
      </div>

      <div class="item-formulario">
        <label for="endereco">Endereço:</label>
        <input type="text" name="endereco" id="endereco" v-model="usuario.endereco" />
      </div>

      <div class="layout-3-2">
        <div class="item-formulario" id="area-cidade">
          <label for="cidade">Cidade:</label>
          <input type="text" name="cidade" id="cidade" v-model="usuario.cidade" />
        </div>

        <div class="item-formulario" id="area-estados">
          <label for="slct-estados">Estado:</label>
          <select name="slctEstados" id="slct-estados" v-model="usuario.estadoSelecionado">
            <option value="" disabled>Selecione seu estado</option>
            <option v-for="estado of estados" :key="estado.uf" :value="estado.uf">
              {{ estado.nome }}
            </option>
          </select>
        </div>

        <div class="item-formulario" id="area-data-nascimento">
          <label for="data-nascimento">Data de nascimento:</label>
          <input type="date" name="dataNascimento" id="data-nascimento" v-model="usuario.dataNascimento" />
        </div>

        <div class="item-formulario" id="area-hobbies">
          <label for="hobbies">Hobbies:</label>
          <input type="text" name="hobbies" id="hobbies" v-model="usuario.hobbies" />
        </div>

        <div class="item-formulario" id="area-linguagens-programacao">
          <label for="linguagens-programacao">Linguagens de programação:</label>
          <input
            type="text"
            name="linguagensProgramacao"
            id="linguagens-programacao"
            v-model="usuario.linguagensProgramacao"
          />
        </div>
      </div>

      <div class="item-formulario">
        <label for="biografia">Biografia:</label>
        <textarea
          name="biografia"
          id="biografia"
          cols="25"
          rows="10"
          v-model="usuario.biografia"
        ></textarea>
      </div>

      <button type="submit">{{ textoBotao }}</button>
    </form>
  </div>
</template>

<style scoped>

.container-formulario {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 20px;
  gap: 20px;
}

.formulario {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 15px;
  max-width: 800px; 
  width: 100%;
}

.item-formulario {
  display: flex;
  flex-direction: column;
  gap: 5px;
}

input,
select,
textarea {
  width: 100%;
  padding: 10px;
  border-radius: 8px;
  border: 1px solid #d0d0d0;
  background-color: #fafafa;
}

#area-confirmar-senha,
#area-email,
#area-data-nascimento {
  display: flex;
  justify-content: flex-end;
}

#data-nascimento {
  width: auto; 
}

#endereco {
  width: auto;
}

select {
  width: auto; 
}

.layout-2-2 {
  grid-template-columns: repeat(2, 1fr);
}

.layout-3-2 {
  grid-template-columns: repeat(2, 1fr);
  grid-template-areas:
    'cidade estado data-nascimento'
    'hobbies . linguagens-programacao';
}

#area-cidade {
  grid-area: cidade;
}

#area-estados {
  grid-area: estado;
}

#area-data-nascimento {
  grid-area: data-nascimento;
}

#area-hobbies {
  grid-area: hobbies;
}

#area-linguagens-programacao {
  grid-area: linguagens-programacao;
}

button {
  padding: 10px 20px;
  border-radius: 8px;
  border: none;
  background-color: #007bff;
  color: #fff;
  font-size: 16px;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}

@media (max-width: 768px) {
  .formulario {
    grid-template-columns: 1fr; 
  }

  #area-confirmar-senha,
  #area-email,
  #area-data-nascimento {
    justify-content: center;
  }
}
</style>
