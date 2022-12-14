<template>
  <h5>User</h5>

  {{ user.first_name }}
  {{ user.last_name }}
  <br /><br />
  <h5>Full name</h5>
  {{ fullName }}

  <button @click="user.first_name = 'Maria Luiza'">Atualizar</button>
</template>

<script>
import { ref, computed, watch } from "vue";

export default {
  name: "App",

  setup() {
    const user = ref({
      first_name: "Dimas",
      last_name: "Capelari",
    });

    // Computed para objetos computados
    const fullName = computed(() => {
      return `${user.value.first_name} ${user.value.last_name}`;
    });

    // Watch para observar e executar alguma coisa quando alterado
    watch(
      user,
      () => {
        console.log("Lógica cabulosa");
      },
      {
        deep: true,
      }
    );

    return {
      user,
      fullName,
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
