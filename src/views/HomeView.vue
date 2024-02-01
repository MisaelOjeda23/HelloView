<script setup lang="ts">
import { ref } from 'vue';
import type { Ref } from 'vue';

const nombre: Ref<string> = ref('')
const lastName: Ref<string> = ref('')
const number: Ref<string> = ref('')
const age: Ref<string> = ref('')
const genre: Ref<string> = ref('')
const message: Ref<string> = ref('')
const val:Ref<string> = ref('hidden')

const nameValid = () => { 
  if (nombre.value.length > 18) {
    val.value = 'hidden'
    return 'perro'
  } else {
    return 'success'
  }
}

const lastNameValid = () => { 
  if (lastName.value.length > 18) {
    val.value = 'hidden'
    return 'perro'
  } else {
    return 'success'
  }
}

const checkValidation = () => {

  const ageNumber = parseInt(age.value);
  console.log('clicked')

  if ([nombre.value, lastName.value, number.value, age.value, genre.value].includes('')) {
    message.value = 'Todos los campos obligatorios'
    val.value = 'hidden'
  } else {
    val.value = 'show'
  }

  if (nombre.value.length >= 18 || lastName.value.length >= 18) {
    message.value = 'Nombre o apellido menor a 18 caracteres'
  }

  if (number.value.length != 10 || !/^\d+$/.test(number.value)) {
    message.value = 'Ingresa un número valido'
  }

  if (isNaN(ageNumber) || ageNumber < 0 || ageNumber > 60) {
    message.value = 'Edad entre 0 y 60'
  }

  if (genre.value.length < 0 || genre.value == "1") {
    message.value = 'Seleccione un genero válido'
  }
}

</script>

<template>
  
  <main>
    <article class="form">
      <div class="error-log">
        {{ message }}
      </div>
      <div class="hd">
        <h2>Formita Vue</h2>
      </div>
      <section class="form-body">
        <div class="form-input">
          <label for="nombre">Nombre</label>
          <input :class="nameValid()" placeholder="Ej: Manuel" type="text" v-model="nombre">
          <span :class="nombre.length < 18 ? 'hidden' : 'show'">No más de 18 caracteres</span>
        </div>
        <div class="form-input">
          <label for="lastName">Apellido</label>
          <input :class="lastNameValid()" placeholder="Ej: Ramirez" type="text" v-model="lastName">
          <span :class="lastName.length < 18 ? 'hidden' : 'show'">No más de 18 caracteres</span>
        </div>
        <div class="form-input">
          <label for="number">Número telefónico</label>
          <input :class="number.length === 10 ? 'success' : 'perro' " placeholder="Ej: 9933009988" type="text" v-model="number">
          <span :class="number.length <= 0 || number.length === 10 ? 'hidden' : 'show'">Ingresa un número válido</span>
        </div>
        <div class="form-input">
          <label for="age">Edad</label>
          <input class="success" placeholder="Ej: 20" type="number" v-model="age">
        </div>
        <div class="select form-input">
          <label for="genre">Género</label>
          <select class="success" name="Genero" id="" v-model="genre">
            <option disabled value="1">Selecciona Genero...</option>
            <option value="Mujer">Mujer</option>
            <option value="Hombre">Hombre</option>
          </select>
        </div>
      </section>
      <div class="btn-cont">
        <button @click="checkValidation()" class="btn" type="submit">Enviar</button>
      </div>
    </article>
    <article>
      <div :class="val">
        <div class="values">
          <h1>{{ nombre + ' ' + lastName }}</h1>
          <p class="items"> {{ age }} Años</p>
          <p class="items"> {{ genre }} </p>
          <p class="items"> Número telefónico: {{ number }} </p>
        </div>
      </div>  
    </article>
  </main>
</template>

<style>
h1 {
  font-size: 30px;
  font-weight: bold;
  color: #6e1fca;
  margin-bottom: 10px;
}

h2 {
  font-size: 25px;
}

span {
  font-size: small;
  font-weight: 500;
  color: #dc023c;
  margin-top: 3px;
  background-color: #ffacc2;
  border-radius: 30px;
}

label {
  font-size: 12px;
  font-weight: 500;
  color: #9702dc;
  margin-top: 3px;
  border-radius: 30px;
}

.items {
  margin-bottom: 10px;
  padding: .5rem 1rem;
  font-size: 15px;
  font-weight: 700;
  color: #52b42e;
  margin-top: 3px;
  background-color: #7bfdc53f;
  border-radius: 30px;
}

.form, .values {
  margin-right: 20px;
  background-color: #e9dafa;
  padding: 20px;
  border-radius: 15px;
  border: 3px blueviolet solid;
  min-width: 350px;
}

.perro {
  color: rgb(196, 195, 195);
}

.success {
  color: violet;
}

.hidden {
  display: none;
}

.show {
  display: block;
}

input, select {
  border-color: #d480ed;
  font-weight: bold;
  margin: 5px;
  padding: 10px;
  border-radius: 20px;
}

.error-log {
  display: flex;
  flex-direction: column;
  font-size: small;
  text-align: center;
  font-weight: 500;
  color: #dc023c;
  margin-top: 3px;
  background-color: #ffacc2;
  border-radius: 30px;
}

.form-input {
  display: flex;
  flex-direction: column;
  text-align: center;
  padding: auto;
  margin: 10px 20px;
}

.select {
  display: flex;
  flex-direction: column;
}

.btn {
  border: none;
  border-radius: 20px;
  color: #ffff;
  background-color: rgb(174, 59, 232);
  padding: 10px;
  font-size: 15px;
  cursor: pointer;
}

.btn:disabled {
  background-color: rgb(216, 180, 231);
  cursor: not-allowed;
}

.hd {
  text-align: center;
  padding: 2px;
  margin-bottom: 40px;
  margin-top: 20px;
  background-color: blueviolet;
  border-radius: 25px;
  color: #ffff;
}

.btn-cont {
  display: flex;
  flex-direction: column;
  margin: 20px;
}

.form-body {
  margin-top: 15px;
  display: flex;
  flex-direction: column;
}

</style>

