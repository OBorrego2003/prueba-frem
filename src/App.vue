<template>
  <div>
    
    
    <form @submit.prevent="registerUser" class="user-form">
      <h1>Registro</h1>
      <div class="form-group">
        <label for="username">Nombre de Usuario:</label>
        <input v-model="newUser.username" type="text" required />
        <label for="email">Correo Electrónico:</label>
        <input v-model="newUser.email" type="email" required />
        <label for="age">Fecha de Nacimiento:</label>
        <input v-model="newUser.age" type="date" required />
        <label for="password">Contraseña:</label>
        <input v-model="newUser.password" type="password" required />
      </div>
      <button type="submit">Registrar</button>
    </form>
    
    <div class="user-list">
      <h2>Lista de Usuarios Registrados</h2>
      <ul>
        <li v-for="(user, index) in users" :key="index">
          {{ user.username }} - {{ user.email }} - {{ user.age }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newUser: {
        username: '',
        email: '',
        age: '',
        password: ''
      },
      users: []
    };
  },
  methods: {
    registerUser() {
      this.users.push({ ...this.newUser });
      
      this.newUser.username = '';
      this.newUser.email = '';
      this.newUser.age = '';
      this.newUser.password = '';
    }
  }
};
</script>

<style>
.user-form {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: 20px;
  border: #369f72 1px solid;
}
.form-group {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: 20px;
  padding: 10px;
}

.button{
  background-color: #369f72;
  color: white;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}
.button:hover {
  background-color: #369f72;
}

.user-list {
  margin-top: 20px;
}

.user-list ul {
  list-style-type: none;
  padding: 0;
}

.user-list li {
  padding: 5px 0;
  border-bottom: 1px solid #ccc;
}
</style>