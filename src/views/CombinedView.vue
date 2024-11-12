<style scoped>
/* Estilos generales */
.title {
    font-size: 2rem;
    font-weight: bold;
    color: #154189;
    margin-bottom: 20px;
    text-align: center;
}

.input-group {
    display: flex;
    justify-content: center;
    align-items: center;
    margin-top: 10px;
}

.task-input {
    padding: 10px;
    width: 250px;
    border-radius: 25px 0 0 25px;
    border: 1px solid #ccc;
    border-right: none;
    outline: none;
    box-shadow: 0 0 5px rgba(30, 144, 255, 0.5);
}

.add-button {
    padding: 10px 20px;
    background: linear-gradient(90deg, #00bcd4, #4caf50); /* Gradiente de la barra de navegación */
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
    display: flex;
    flex-direction: column;
    align-items: center;
}

.task-card {
    border: 1px solid #ddd;
    padding: 15px;
    border-radius: 10px;
    margin: 10px 0;
    background-color: #f9f9f9;
    width: 90%;
    max-width: 500px;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
    text-align: center;
}

.task-content {
    display: flex;
    flex-direction: column;
    align-items: center;
}

h5 {
    font-size: 1.2em;
    margin: 10px 0;
    font-weight: bold;
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




