<template>
    <div class="add-task-container">
        <h1 class="title">Añadir Tarea</h1>
        <div class="input-group">
            <input 
                v-model="newTask" 
                @keyup.enter="addTask" 
                placeholder="Añadir nueva tarea" 
                class="task-input"
            />
            <button @click="addTask" class="add-button">Añadir</button>
        </div>

        <div v-if="tasks.length > 0" class="task-list">
            <div v-for="task in tasks" :key="task.id" class="task-item">
                <div class="task-content">
                    <span class="task-text">{{ task.todo }}</span>
                    <span class="task-status" :class="{ completed: task.completed }">
                        {{ task.completed ? 'Completado' : 'Pendiente' }}
                    </span>
                </div>
                <div class="task-buttons">
                    <button @click="toggleTaskCompletion(task)" class="complete-button">
                        <span v-if="task.completed">✔️</span>
                        <span v-else>✔️</span>
                    </button>
                    <button @click="deleteTask(task)" class="delete-button">
                        🗑️
                    </button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "AddTask",
    data() {
        return {
            newTask: "",
            tasks: [],
        };
    },
    methods: {
        addTask() {
            if (this.newTask.trim() === "") return;

            const newTask = {
                todo: this.newTask,
                completed: false,
                id: Date.now(),
            };

            this.tasks.unshift(newTask);
            this.newTask = "";
        },
        deleteTask(task) {
            this.tasks = this.tasks.filter((t) => t.id !== task.id);
        },
        toggleTaskCompletion(task) {
            task.completed = !task.completed;
        },
    },
};
</script>

<style scoped>
.add-task-container {
    padding: 20px;
    max-width: 500px;
    margin: 0 auto;
    text-align: center;
}

.title {
    font-size: 2rem;
    font-weight: bold;
    color: #154189;
    margin-bottom: 20px;
}

.input-group {
    display: flex;
    justify-content: center;
    align-items: center;
    margin-top: 10px;
}

.task-input {
    width: 100%;
    max-width: 350px;
    padding: 10px 15px;
    border: 1px solid #dcdcdc;
    border-radius: 25px 0 0 25px;
    font-size: 1rem;
    outline: none;
    box-shadow: 0 0 5px rgba(30, 144, 255, 0.5);
    border-right: none;
}

.add-button {
    padding: 10px 20px;
    background-color: #1e90ff;
    color: white;
    border: none;
    border-radius: 0 25px 25px 0;
    font-size: 1rem;
    font-weight: bold;
    cursor: pointer;
    transition: background-color 0.3s;
    box-shadow: 0 0 5px rgba(30, 144, 255, 0.5);
}

.add-button:hover {
    background-color: #0073e6;
}

.task-list {
    margin-top: 20px;
}

.task-item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 15px;
    border: 1px solid #ddd;
    border-radius: 10px;
    margin-bottom: 10px;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}

.task-content {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
}

.task-text {
    font-size: 1.2rem;
    font-weight: bold;
    color: #333;
}

.task-status {
    font-size: 0.9rem;
    font-weight: bold;
    color: #fff;
    background-color: #f0ad4e;
    padding: 5px 10px;
    border-radius: 5px;
    margin-top: 5px;
}

.task-status.completed {
    background-color: #5cb85c; /* Verde para tareas completadas */
}

.task-buttons {
    display: flex;
    gap: 10px;
}

.complete-button, .delete-button {
    border: 2px solid;
    border-radius: 5px;
    padding: 8px;
    font-size: 1.1rem;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
}

.complete-button {
    color: #5cb85c;
    border-color: #5cb85c;
}

.delete-button {
    color: #d9534f;
    border-color: #d9534f;
}
</style>

