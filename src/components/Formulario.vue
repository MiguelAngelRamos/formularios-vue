<template>
  <div class="container mt-5 col-4 offset-4">
    <form @submit.prevent="submitFormulario">
      <!-- Input -->
      <div class="mb-3">
        <label for="idNombre" class="form-label">Nombre</label>
        <input type="text" class="form-control" id="idNombre" v-model.trim="miFormulario.nombre" />

        <div v-if="nombreVacio && !miFormulario.nombre" id="emailHelp" class="form-text text-danger">
          El nombre es requerido.
        </div> 

      </div>

      <div class="mb-3">
        <label for="idSaldo" class="form-label">Saldo</label>
        <input type="number" class="form-control" id="idSaldo" v-model.number="miFormulario.saldo"/>
      </div>
      <!-- /Input -->

      <!-- Check -->
      <div class="mb-3 form-check">
        <input type="checkbox" class="form-check-input" id="idCheck1" value="javascript" v-model="miFormulario.categorias"/>
        <label class="form-check-label" for="idCheck1">JavaScript</label>
      </div>

      <div class="mb-3 form-check">
        <input type="checkbox" class="form-check-input" id="idCheck2" value="python" v-model="miFormulario.categorias"/>
        <label class="form-check-label" for="idCheck2">Python</label>
      </div>
      <!-- /Check -->

      <!-- Radio -->
      <div class="form-check">
        <input
          class="form-check-input"
          type="radio"
          name="flexRadioDefault"
          id="flexRadioDefault1"
          value="desarrollo"
          v-model="miFormulario.estado"
        />
        <label class="form-check-label" for="flexRadioDefault1">
          Desarrollo
        </label>
      </div>

      <div class="form-check">
        <input
          class="form-check-input"
          type="radio"
          name="flexRadioDefault"
          id="flexRadioDefault2"
          v-model="miFormulario.estado"
          value="produccion"
        />
        <label class="form-check-label" for="flexRadioDefault2">
          Producción
        </label>
      </div>
      <br>
      <!-- /Radio -->

      <!-- Select -->
      <select class="form-select" v-model="miFormulario.pelicula">
        <option value="rocky">Rocky</option>
        <option value="ironman">Ironman</option>
        <option value="superman">Superman</option>
        <option value="hulk">Hulk</option>
      </select>
      <!-- /Select -->
      <br>
      <button type="submit" class="btn btn-primary" :disabled="bloquear">Submit</button>
    </form>

    <br>
     En el modelo: 
      <br>
    <pre>
     
      {{ miFormulario }}
    </pre>
  </div>

  <!-- Nombre, Saldo, Categorias (check), Radios (Estado), Select(Peliculas), Button Submit -->
</template>

<script>
export default {
  data() {
    return {
      miFormulario: {
        nombre: "",
        saldo: 0,
        categorias: [],
        estado: "",
        pelicula: "rocky"
      },
      nombreVacio: false
    }
  },
  methods: {
    submitFormulario() {
      // lo que enviamos a la base de datos el objeto
      console.log(this.miFormulario);

      if (this.miFormulario.nombre.trim() === "") {
        console.log("Campo Vacio");
        this.nombreVacio = true;
        return
      }
      console.log("Campo nombre con información");

      // Resetear Formulario
      this.miFormulario = {
        nombre: "",
        saldo: 0,
        categorias: [],
        estado: "",
        pelicula: "rocky"
      }
    }
  },
  computed: {
    bloquear() {
      // return this.miFormulario.nombre.trim() ==="" ? true: false;
      // vamos usar este método para bloquear el botón submit
      return this.nombreVacio && !this.miFormulario.nombre? true: false
    }
  }
};
</script>

<style></style>
