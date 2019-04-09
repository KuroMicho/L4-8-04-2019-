<template>
    <div>
        <h1>Hola {{ msg }}</h1>
        <button type="button" class="btn btn-primary">Primary</button>
        <b-button variant="primary">Button</b-button>
        <div>
  <b-card
    title="nombre"
    img-src="https://picsum.photos/600/300/?image=25"
    img-alt="Image"
    img-top
    tag="article"
    style="max-width: 20rem;"
    class="mb-2"
  >
    <b-card-text>
      Some quick example text to build on the card title and make up the bulk of the card's content.
    </b-card-text>

    <b-button href="#" variant="primary">Go somewhere</b-button>
  </b-card>
</div>
    </div>
    
</template>

<script>
    export default {
        data(){
            return {
                msg: "El Kevo"
            }
        }
    }
</script>

<style>

</style>
