<template>
  <div>
    <div class="row mt-3">
      <div class="col-xs-6">
        <h4>Lista de Productos</h4>
      </div>
    </div>

    <div class="row mt-4">
      <div class="col-sm-12">
        <b-table responsive striped hover :fields="fields" :items="items"/>
      </div>
    </div>
    <div class="col sm-6 ml-20">
      <b-button variant="primary" href="/productos/nuevo">Nuevo</b-button>
    </div>
  </div>
</template> 
/* dfef */

<script>
import firebase, { db } from "../../services/firebase";

export default {
  asyncData() {
    return db
      .collection("Productos")
      .get()
      .then(res => {
        let items = [];
        res.forEach(value => {
          items.push(value.data());
        }); console.log(items)
        return {
          items
        };
      });
  },
  data() {
    return {
      fields: ["Imagen", "Nombre", "Precio", "Cantidad", "Acciones"]
    };
  }
};
</script>

