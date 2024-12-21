<template>
  <img
    :src="imagen"
    alt="no se puede ver la imagen"
  />
  <input v-model="pregunta" type="text" placeholder="Marca de agua" />
  <p>Recuerda que cuando finalices tu pregunta dar un ?</p>
  <h1>{{ pregunta }}</h1>
  <h2>{{respuesta}}</h2>
</template>

<script>
export default {
  data() {
    return {
      pregunta: "¿Tienes manos?",
      respuesta: null,
      imagen:'https://yesno.wtf/assets/yes/14-b57c6dc03aa15a4b18f53eb50d6197ee.gif'
    };
  },
  watch: {
    pregunta(value, oldValue) {
      console.log(value);
      console.log(oldValue);
      if (value.includes("?")) {
        //programar la llamada del api para obtener el si o no y la img
        console.log("Aqui llamo al api");
        this.fachada();
      }
    },
    
  },
  methods: {
    async llamarAPI() {
      const data = await fetch("https://yesno.wtf/api").then((resp) => resp.json());
      this.respuesta= data.answer;
      this.imagen=data.image;
      console.log(data);
    },
    async fachada(){
        await this.llamarAPI();
    }
  },
};
</script>

<style>
</style>