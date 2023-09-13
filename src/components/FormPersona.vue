<template>
  <div class="modal" id="formPersona" tabindex="-1" role="dialog">
    <div class="modal-dialog" role="document">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title">Nueva Persona</h5>
          <button
            class="btn-close"
            data-bs-dismiss="modal"
            aria-label="close"
          ></button>
        </div>
        <div class="modal-body">
          <form @submit.prevent="agregarPersona">
            <div class="column">
              <div class="col-md-1">
                <label for="nombre" class="form-label text-end">Nombre</label>
              </div>
              <div class="col-md-12 mb-3">
                <input
                  type="text"
                  class="form-control"
                  id="nombre"
                  v-model="model.nombre"
                  required
                />
              </div>
              <div class="col-md-1">
                <label for="correo" class="form-label text-end">Correo</label>
              </div>
              <div class="col-md-12 mb-3">
                <input
                  type="email"
                  class="form-control"
                  id="correo"
                  v-model="model.correo"
                  required
                />
              </div>
              <div class="col-md-1">
                <label for="celular" class="form-label text-end">Celular</label>
              </div>
              <div class="col-md-12 mb-3">
                <input
                  type="tel"
                  class="form-control"
                  id="celular"
                  v-model="model.celular"
                  required
                />
              </div>
              <div class="col-md-1">
                <label for="edad" class="form-label text-end">Edad</label>
              </div>
              <div class="col-md-12 mb-3">
                <input
                  type="number"
                  class="form-control"
                  id="edad"
                  v-model="model.edad"
                  required
                />
              </div>
              <div class="row mb-12">
                <div class="col-md-3">
                  <div class="form-check form-check-lg">
                    <input
                      type="checkbox"
                      class="form-check-input"
                      id="estado"
                      v-model="model.estado"
                      required
                    />
                    <label for="estado" class="form-check-label">Estado</label>
                  </div>
                </div>
              </div>
            </div>
          </form>
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-danger" data-bs-dismiss="modal">
            Cerrar
          </button>
          <button type="submit" class="btn btn-primary" @click="agregarPersona">
            Guardar
          </button>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "modalpersona",
  props: {
    persona: Object,
  },
  data() {
    return {
      model: {
        nombre: null,
        correo: null,
        celular: null,
        edad: null,
        estado: null,
      },
    };
  },
  methods: {
    agregarPersona() {
      this.$emit("guardarPersona", this.model);
    },
    resetForm() {
      this.model = {
        nombre: null,
        correo: null,
        celular: null,
        edad: null,
        estado: null,
      };
    },
    abrirModal(personaEditar) {
      if (personaEditar) {
        this.model.nombre = personaEditar.nombre;
        this.model.correo = personaEditar.correo;
        this.model.celular = personaEditar.celular;
        this.model.edad = personaEditar.edad;
        this.model.estado = personaEditar.estado;
      } else {
        this.resetForm();
      }
    },
  },
  mounted() {
    this.abrirModal();
  },
};
</script>
