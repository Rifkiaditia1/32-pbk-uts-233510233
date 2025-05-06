<template>
  <div class="app">
    <div class="card">
      <h1 class="title">📝 Daftar Kegiatan</h1>

      <div class="input-container">
        <input
          v-model="newTask"
          @keyup.enter="addTask"
          placeholder="Tambah kegiatan baru..."
          class="input"
        />
        <button @click="addTask" class="btn">Tambah</button>
      </div>

      

      <ul class="task-list">
        <li
          v-for="(task, index) in filteredTasks"
          :key="index"
          
        >
          
          <span class="task-text">{{ task.text }}</span>
          
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTask: '',
      tasks: [],
      
    }
  },
  computed: {
    filteredTasks() {
      return this.showOnlyIncomplete
        ? this.tasks.filter(task => !task.done)
        : this.tasks;
    }
  },
  methods: {
    addTask() {
      if (this.newTask.trim()) {
        this.tasks.push({ text: this.newTask.trim(), done: false });
        this.newTask = '';
      }
    
    }
  }
}
</script>

