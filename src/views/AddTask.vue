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
    background: linear-gradient(90deg, #00bcd4, #4caf50); /* Verde agua, igual que la barra de navegación */
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
    background: linear-gradient(90deg, #00bcd4, #4caf50); /* Mantener el mismo gradiente en el hover */
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


