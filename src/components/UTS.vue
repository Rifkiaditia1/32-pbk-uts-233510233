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
  
        <div class="filter">
          <label>
            <input type="checkbox" v-model="showOnlyIncomplete" />
            Tampilkan hanya yang belum selesai
          </label>
        </div>
  
        <ul class="task-list">
          <li
            v-for="(task, index) in filteredTasks"
            :key="index"
            class="task-item"
            :class="{ done: task.done }"
          >
            <input type="checkbox" v-model="task.done" />
            <span class="task-text">{{ task.text }}</span>
            <button @click="removeTask(index)" class="delete-btn">🗑</button>
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
        showOnlyIncomplete: false
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
      },
      removeTask(index) {
        this.tasks.splice(index, 1);
      }
    }
  }
  </script>
  
  <style scoped>
  @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600&display=swap');
  
  body {
    margin: 0;
    font-family: 'Inter', sans-serif;
    background: linear-gradient(to right, #8e9eab, #eef2f3);
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  
  .app {
    padding: 20px;
    width: 100%;
    max-width: 600px;
  }
  
  .card {
    background: white;
    border-radius: 16px;
    box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
    padding: 30px;
    transition: 0.3s;
  }
  
  .title {
    text-align: center;
    margin-bottom: 25px;
    color: #333;
    font-size: 28px;
  }
  
  .input-container {
    display: flex;
    gap: 10px;
    margin-bottom: 20px;
  }
  
  .input {
    flex: 1;
    padding: 12px 16px;
    border-radius: 10px;
    border: 1px solid #ccc;
    font-size: 16px;
    transition: 0.3s;
  }
  
  .input:focus {
    border-color: #4caf50;
    outline: none;
  }
  
  .btn {
    padding: 12px 18px;
    background-color: #4caf50;
    color: white;
    border: none;
    border-radius: 10px;
    cursor: pointer;
    font-weight: 600;
    transition: 0.3s;
  }
  
  .btn:hover {
    background-color: #43a047;
  }
  
  .filter {
    margin-bottom: 15px;
    font-size: 14px;
    color: #555;
  }
  
  .task-list {
    list-style: none;
    padding: 0;
    margin: 0;
  }
  
  .task-item {
    display: flex;
    align-items: center;
    gap: 12px;
    background: #f9f9f9;
    padding: 12px 16px;
    border-radius: 10px;
    margin-bottom: 10px;
    transition: 0.3s;
  }
  
  .task-item.done {
    background-color: #d4edda;
  }
  
  .task-text {
    flex-grow: 1;
    font-size: 16px;
    transition: 0.2s;
  }
  
  .task-item.done .task-text {
    text-decoration: line-through;
    color: #777;
  }
  
  .delete-btn {
    background: none;
    border: none;
    font-size: 18px;
    cursor: pointer;
    color: #e74c3c;
    transition: transform 0.2s;
  }
  
  .delete-btn:hover {
    transform: scale(1.2);
  }
  </style>
  