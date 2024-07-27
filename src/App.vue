<script setup>
import { ref } from 'vue'
import ComponenteDados from './components/ComponenteDados.vue'
import ComponenteRegistro from './components/ComponenteRegistro.vue'

const mostrarDados = ref(false)

const usuario = ref({ nome: '' })

function handleFormularioEnviado(usuarioAtualizado) {
  mostrarDados.value = !mostrarDados.value
  usuario.value = usuarioAtualizado
}

</script>

<template>
  <div class="container">
    <ComponenteRegistro
      class="componente-registro"
      title="Projeto 2: Componentes"
      @formularioEnviado="handleFormularioEnviado"
    />
    <ComponenteDados :usuario="usuario" class="componente-dados" v-if="mostrarDados" />
  </div>
</template>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.container {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: flex-start;
  padding: 20px;
  gap: 20px;
}

.componente-dados,
.componente-registro {
  flex: 1;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  background-color: #ffffff;
}

.componente-dados {
  width: calc(50% - 10px);
}

.componente-registro {
  width: calc(50% - 10px);
}

@media (max-width: 768px) {
  .container {
    flex-direction: column;
  }

  .componente-dados,
  .componente-registro {
    width: 100%;
  }
}
</style>
