<script setup lang="ts">
import { ref } from 'vue';
import type { Ref } from 'vue';

const nombre: Ref<string> = ref('')
const lastName: Ref<string> = ref('')
const number: Ref<string> = ref('')
const age: Ref<string> = ref('')
const genre: Ref<string> = ref('')
const error: Ref<boolean> = ref(true)

const nameValid = () => { nombre.value.length > 18 }
const lastNameValid = () => { lastName.value.length > 18 }
const numberValid = () => { number.value.length == 10 && /^\d+$/.test(number.value) }
const isAgeValid = () => {
  const ageNumber = parseInt(age.value);
  return !isNaN(ageNumber) && ageNumber >= 1 && ageNumber <= 60;
};

</script>

<template>
  <main>
    <div class="hd">
      <h2>Formita Vue</h2>
    </div>
    <section class="form-body">
      <div>
        <input :class="{ error: nameValid(), success: nameValid() }" placeholder="Nombre" type="text" v-model="nombre">
      </div>
      <div>
        <input placeholder="Apellido" type="text" v-model="lastName">
      </div>
      <div>
        <input placeholder="Número Telefónico" type="text" v-model="number">
      </div>
      <div>
        <input placeholder="Edad" type="number" v-model="age">
      </div>
      <div class="select">
        <select placeholder="Genero" name="Genero" id="">
          <option value="1">Mujer</option>
          <option value="2">Hombre</option>
        </select>
      </div>
    </section>
    <div class="btn-cont">
      <button class="btn" type="submit" :disabled="!(nombre.length > 0 && lastName.length > 0 && number.length > 0 && genre.length > 0)">Enviar</button>
    </div>
  </main>
</template>

<style>

h2 {
  font-size: 25px;
}

.error {
  color: red;
}

.success {
  color: violet;
}

input {
  border-color: #d480ed;
  font-weight: bold;
  margin: 10px;
  padding: 10px;
  border-radius: 20px;
}

select {
  max-width: 100%;
  border-color: #d480ed;
  font-weight: bold;
  margin: 10px;
  padding: 10px;
  border-radius: 20px;
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

.btn:disabled{
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

.error {
  display: none;
}

</style>

