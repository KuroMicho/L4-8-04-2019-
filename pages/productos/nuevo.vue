<template>
  <b-form @submit.prevent="guardarProducto">
    <h1>Nuevo Producto</h1>
    <div class="row">
      <div class="col-sm-12">
        <b-form-group label="Imagen:" label-for="imagen">
          <b-form-file
            id="imagen"
            placeholder="Load Image"
            v-model="form.Imagen"
            drop-placeholder="Load Image"
          />
        </b-form-group>

        <b-form-group label="Nombre:" label-for="nombre">
          <b-form-input
            id="Nombre"
            placeholder="Nombre del producto"
            v-model="form.Nombre"
            required
          />
        </b-form-group>

        <b-form-group label="Precio:" label-for="precio">
          <b-form-input
            id="Precio"
            type="text"
            v-model="form.Precio"
            required
            placeholder="Precio del producto"
          />
        </b-form-group>

        <b-form-group label="Cantidad:" label-for="cantidad">
          <b-form-input
            id="Cantidad"
            type="number"
            v-model="form.Cantidad"
            required
            placeholder="Cantidad del producto"
          />
        </b-form-group>
      </div>
    </div>

    <b-button-toolbar>
      <b-button-group right class="mx-2">
        <b-button href="/productos">Volver</b-button>
        <b-button variant="primary" type="submit" :disabled="guardando">Guardar</b-button>
        <div style="margin-inline:40px">
          <b-spinner variant="primary" v-if="guardando"></b-spinner>
        </div>
      </b-button-group>
    </b-button-toolbar>
  </b-form>
</template>

<script>
import { db } from "../../services/firebase.js";

export default {
  data() {
    return {
      form: {
        Nombre: "",
        Cantidad: "",
        Precio: ""
      },
      guardando: false
    };
  },
  methods: {
    guardarProducto() {
      this.guardando = true;
      db.collection("Productos")
        .add(this.form)
        .then(res => {
          alert("guardando");
          this.$router.push({ path: "/productos" }); //navegar en toda la aplicacion.
        });
    }
  }
};
</script>
