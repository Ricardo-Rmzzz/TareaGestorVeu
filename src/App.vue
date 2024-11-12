<template>
  <div id="app">
    <!-- Barra de navegación personalizada -->
    <nav class="navbar navbar-expand-lg navbar-custom">
      <div class="container-fluid">
        <!-- Logo y nombre de la marca -->
        <a class="navbar-brand" href="#">
          <i class="fab fa-vuejs"></i>
          <span>Gestor de Tareas</span>
        </a>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNavAltMarkup" aria-controls="navbarNavAltMarkup" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
          <div class="navbar-nav ms-auto">
            <router-link class="nav-link" to="/">
              <i class="fas fa-home"></i> Inicio
            </router-link>
            <router-link class="nav-link" to="/addtask">
              <i class="fas fa-star"></i> Agregar Tarea
            </router-link>
            <router-link class="nav-link" to="/tasklist">
              <i class="fas fa-star"></i> Lista de Tareas
            </router-link>
            <router-link class="nav-link" to="/combinedview">
              <i class="fas fa-star"></i> Vista Combinada
            </router-link>
          </div>
        </div>
      </div>
    </nav>

    <!-- Contenedor de vista de enrutador -->
    <router-view/>
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.navbar-custom {
  background: linear-gradient(90deg, #00bcd4, #4caf50); /* Verde agua */
  padding: 15px;
  color: #fff;
}

.navbar-brand {
  font-size: 1.5rem;
  font-weight: bold;
  color: #fff;
  display: flex;
  align-items: center;
}

.navbar-brand i {
  color: #87CEEB;
  margin-right: 8px;
}

.navbar-nav .nav-link {
  color: #ffffff;
  font-size: 1.1rem;
  font-weight: bold;
  margin-right: 15px;
  display: flex;
  align-items: center;
}

.navbar-nav .nav-link i {
  margin-right: 5px;
}

.navbar-nav .router-link-exact-active {
  color: #FFD700; /* Color dorado para el enlace activo */
}

.navbar-nav .nav-link:hover {
  color: #FFD700; /* Hover dorado */
}
</style>

