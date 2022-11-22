<template>
  <main>
    <h1>Lista de tarefas</h1>
    <p>Adicione itens a sua lista de tarefa</p>

    <div class="create-new">
      <input
        type="text"
        v-model="newTask"
        placeholder="Adicione tarefa"
        @keypress.enter="addTask"
      />
      <button @click="addTask">Add</button>
    </div>
    <div class="tasks">
      <task v-for="(task, i) in $store.state.tasks" :key="i" :task="task" />
    </div>
  </main>
</template>

<script>
export default {
  data() {
    return {
      newTask: "",
    };
  },
  methods: {
    addTask() {
      if (this.newTask) {
        this.$store.commit("ADD_TASK", this.newTask);
        this.newTask = "";
      }
    },
  },
};
</script>
