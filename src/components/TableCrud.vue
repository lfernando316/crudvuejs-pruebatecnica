<template>
  <div class="container mt-4">
    <h1>Listado de personas</h1>
    <button
      class="mb-2 bg-success btn btn-succees float-end"
      @click="abrirModal()"
    >
      <i class="fas fa-plus"></i>
    </button>
    <table class="table table-bordered">
      <thead class="bg-primary text-center">
        <tr>
          <th class="bg-primary text-white">Nombre</th>
          <th class="bg-primary text-white">Correo</th>
          <th class="bg-primary text-white">Celular</th>
          <th class="bg-primary text-white">Edad</th>
          <th class="bg-primary text-white">Estado</th>
          <th class="bg-primary text-white">Acciones</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(item, index) in datos" :key="index">
          <td>{{ item.nombre }}</td>
          <td>{{ item.correo }}</td>
          <td>{{ item.celular }}</td>
          <td>{{ item.edad }}</td>
          <td>{{ item.estado }}</td>
          <td>
            <button class="btn btn-primary" @click="abrirModal(index)">
              <i class="fas fa-pencil-alt" />
            </button>
            <button class="btn btn-danger" @click="eliminarItem(index)">
              <i class="fas fa-trash" />
            </button>
          </td>
        </tr>
      </tbody>
    </table>
    <div class="class container mt-3">
      <div class="class text-end">
        <p>Total de registros: {{ contador }}</p>
      </div>
    </div>
    <FormPersona
      ref="formPersona"
      @guardarPersona="guardarPersona"
      :persona="personaEditar"
    />
  </div>
</template>

<script>
import FormPersona from "./FormPersona.vue";
export default {
  name: "tableCrud",
  components: {
    FormPersona,
  },
  data() {
    return {
      contador: 0,
      personaEditar: null,
      datos: [
        {
          nombre: "John Doe",
          correo: "johndoe@example.com",
          celular: "123-456-7890",
          edad: 30,
          estado: "Activo",
        },
      ],
    };
  },
  methods: {
    abrirModal(index) {
      if (index == null) {
        this.$refs.formPersona.resetForm();
        this.personaEditar = null;
      } else {
        this.personaEditar = this.datos[index];
        this.$refs.formPersona.abrirModal(this.personaEditar);
      }
      const modalElement = document.getElementById("formPersona");
      const modal = new bootstrap.Modal(modalElement);
      modal.show();
    },
    guardarPersona(personaGuardar) {
      if (this.personaEditar == null) {
        this.datos.push(personaGuardar);
      } else {
        const index = this.datos.indexOf(this.personaEditar);
        if (index != -1) {
          this.datos[index] = personaGuardar;
        }
      }
      this.personaEditar = null;
      this.countPersonas();
    },
    eliminarItem(index) {
      this.datos.splice(index, 1);
      this.countPersonas();
    },
    countPersonas() {
      this.contador = this.datos.length;
    },
  },
  mounted() {
    this.countPersonas();
  },
};
</script>

<style></style>
