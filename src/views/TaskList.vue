<template>
    <div>
        <h1 class="title">Lista de Tareas</h1>
        <button @click="fetchTasks">Cargar Tareas</button>
        <div v-if="tasks.length > 0">
            <div v-for="task in tasks" :key="task.id" class="task-card">
                <div class="task-content">
                    <h5 :style="{ textDecoration: task.completed ? 'line-through' : 'none' }">{{ task.todo }}</h5>
                    <span class="task-status">{{ task.completed ? 'Completada' : 'Pendiente' }}</span>
                    <div class="task-actions">
                        <button @click="toggleTaskCompletion(task)">
                            {{ task.completed ? 'Desmarcar' : 'Completar' }}
                        </button>
                        <button @click="deleteTask(task)">Eliminar</button>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    name: "TaskList",
    data() {
        return {
            tasks: [], // Almacenamiento local de las tareas traídas de la API
        };
    },
    methods: {
        // Llamada para obtener las tareas desde la API externa
        fetchTasks() {
            axios.get('https://dummyjson.com/todos')
                .then(response => {
                    this.tasks = response.data.todos; // Asumiendo que la API devuelve un objeto con una propiedad "todos"
                })
                .catch(error => {
                    console.error("Error al obtener las tareas:", error);
                });
        },

        // Cambiar el estado de una tarea (completada/no completada)
        toggleTaskCompletion(task) {
            task.completed = !task.completed;
        },

        // Eliminar la tarea seleccionada
        deleteTask(task) {
            this.tasks = this.tasks.filter((t) => t.id !== task.id);
        },
    },

    // Llamada a la API cuando el componente se monta
    mounted() {
        // Esta línea se puede comentar o eliminar si no se quiere cargar automáticamente las tareas al iniciar el componente.
        // this.fetchTasks();
    },
};
</script>

<style scoped>
/* Estilos generales */
.title {
    font-size: 2rem;
    font-weight: bold;
    color: #154189;
    margin-bottom: 20px;
}

button {
    margin-left: 10px;
    padding: 5px 10px;
    background-color: #007bff;
    color: white;
    border: none;
    cursor: pointer;
}

button:hover {
    background-color: #0056b3;
}

/* Estilos para los cuadros de las tareas */
.task-card {
    border: 1px solid #ccc;
    padding: 15px;
    margin: 10px 0;
    border-radius: 8px;
    background-color: #f9f9f9;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.task-content {
    flex: 1;
}

h5 {
    font-size: 1.2em;
    margin: 10px 0;
}

.task-status {
    font-weight: bold;
    margin-left: 10px;
    color: green;
}

.task-status.pendiente {
    color: red;
}

/* Estilo para acciones de la tarea */
.task-actions button {
    margin: 0 5px;
    padding: 5px 10px;
    background-color: #28a745;
    color: white;
    border: none;
    cursor: pointer;
}

.task-actions button:hover {
    background-color: #218838;
}

.task-actions button:last-child {
    background-color: #dc3545;
}

.task-actions button:last-child:hover {
    background-color: #c82333;
}

/* Estilo para tareas completadas */
h5[style*="line-through"] {
    color: #6c757d;
}
</style>
