<template>
    <div>
        <h1 class="title">Lista de Tareas</h1>
        
        <!-- Formulario para agregar tareas -->
        <div>
            <input 
                v-model="newTask" 
                type="text" 
                placeholder="Añadir nueva tarea" 
                @keyup.enter="addTask"
                :disabled="isLoading" 
            />
            <button @click="addTask" :disabled="isLoading">Añadir</button>
        </div>

        <!-- Mostrar las tareas obtenidas de la API -->
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

        <!-- Mensaje de carga -->
        <div v-if="isLoading">Cargando tareas...</div>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    name: "TaskList",
    data() {
        return {
            tasks: [], // Tareas obtenidas de la API
            newTask: "", // Texto de la nueva tarea
            isLoading: false, // Estado de carga
        };
    },
    methods: {
        // Obtener tareas desde la API
        fetchTasks() {
            this.isLoading = true;
            axios.get('https://dummyjson.com/todos')
                .then(response => {
                    this.tasks = response.data.todos;
                })
                .catch(error => {
                    console.error("Error al obtener las tareas:", error);
                })
                .finally(() => {
                    this.isLoading = false;
                });
        },

        // Agregar una nueva tarea
        addTask() {
            if (this.newTask.trim() === "") return; // Validar que la tarea no esté vacía

            // Crear nueva tarea (localmente, sin persistencia en la API en este ejemplo)
            const newTaskObj = {
                id: Date.now(), // Generar ID único
                todo: this.newTask,
                completed: false,
            };

            // Agregar la tarea al principio de la lista
            this.tasks.unshift(newTaskObj); 

            // Limpiar el campo de texto
            this.newTask = "";

            // Si la API soporta agregar tareas, aquí deberías hacer una solicitud POST
            // axios.post('https://dummyjson.com/todos', newTaskObj)
            //   .then(response => {
            //     console.log("Tarea añadida", response.data);
            //   })
            //   .catch(error => {
            //     console.error("Error al añadir la tarea:", error);
            //   });
        },

        // Cambiar el estado de una tarea (completada/no completada)
        toggleTaskCompletion(task) {
            task.completed = !task.completed;
        },

        // Eliminar una tarea seleccionada
        deleteTask(task) {
            this.tasks = this.tasks.filter(t => t.id !== task.id);
        },
    },

    // Llamada a la API cuando el componente se monta
    mounted() {
        this.fetchTasks();
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

input {
    padding: 10px;
    width: 250px;
    margin-right: 10px;
    border-radius: 4px;
    border: 1px solid #ccc;
}

button {
    padding: 10px 15px;
    background-color: #007bff;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
}

button:disabled {
    background-color: #aaa;
    cursor: not-allowed;
}

button:hover {
    background-color: #0056b3;
}

.task-card {
    border: 1px solid #ccc;
    padding: 15px;
    margin: 10px 0;
    border-radius: 8px;
    background-color: #f9f9f9;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
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

.task-status.pendiente {
    color: red;
}
</style>


