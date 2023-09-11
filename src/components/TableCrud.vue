<template>
  <div class="container mt-4">
    <h1>Listado de personas</h1>
    <button
      class="mb-2 bg-success btn btn-succees float-end"
      @click="agregarItem"
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
            <button class="btn btn-primary" @click="editarItem(index)">
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
  </div>
</template>

<script>
export default {
  name: "tableCrud",
  data() {
    return {
      contador: 0,
      datos: [
        {
          nombre: "John Doe",
          correo: "johndoe@example.com",
          celular: "123-456-7890",
          edad: 30,
          estado: "Activo",
        },
        {
          nombre: "John Doe",
          correo: "johndoe@example.com",
          celular: "123-456-7890",
          edad: 30,
          estado: "Activo",
        },
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
    editarItem(index) {},
    eliminarItem(index) {},
    agregarItem() {
      this.datos.push({
        nombre: "Nuevo Nombre",
        correo: "nuevo@correo.com",
        celular: "123-456-7890",
        edad: 30,
        estado: "Activo",
      });
      this.contador = this.datos.length;
    },
  },
};
</script>

<style></style>
