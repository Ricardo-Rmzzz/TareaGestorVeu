<style scoped>
.title {
    font-size: 2rem;
    font-weight: bold;
    color: #154189;
    margin-bottom: 20px;
}

.add-button {
    padding: 10px 20px;
    background: linear-gradient(90deg, #00bcd4, #4caf50); /* Gradiente verde agua, igual que la barra de navegación */
    color: white;
    border: none;
    border-radius: 25px;
    font-size: 1rem;
    font-weight: bold;
    cursor: pointer;
    transition: background-color 0.3s;
    box-shadow: 0 0 5px rgba(30, 144, 255, 0.5);
}

.add-button:hover {
    background: linear-gradient(90deg, #00bcd4, #4caf50); /* Mantener el mismo gradiente en el hover */
}

.task-card {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
    padding: 15px;
    border: 1px solid #ddd;
    border-radius: 10px;
    margin-bottom: 10px;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
    background-color: #f9f9f9;
}

.task-content {
    width: 100%;
    text-align: center;
}

h5 {
    font-size: 1.2em;
    margin: 10px 0;
}

.task-status {
    font-size: 0.9rem;
    font-weight: bold;
    color: #fff;
    background-color: #f0ad4e;
    padding: 5px 10px;
    border-radius: 5px;
}

.task-status.completed {
    background-color: #5cb85c;
}

.task-buttons {
    display: flex;
    justify-content: center;
    gap: 10px;
    margin-top: 10px;
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



