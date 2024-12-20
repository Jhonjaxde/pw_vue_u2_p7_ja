<template>
   <div v-if="esVerdad">
      <h1>Feliz navidad</h1>
    </div>
  <h2>{{ encabezado }}:{{ valor2 }}</h2>
  <p>{{ valor }} <sup>2</sup> ={{ calcularCuadradoComputado }}</p>
  <p>{{ numero }} <sup>2</sup> ={{ calcularCuadradoComputado }}</p>
  
  <div>
    <button @click="incrementar()">+1</button>
    <button v-on:click="decrementar()">-1</button>
    
  </div>
 
</template>

<script>
export default {
  data() {
    return {
      numero: this.valor,
      titulo: "Contador",
    };
  },
  methods: {
    calcularCuadrado() {
      console.log("Entro a calcular");
      return this.numero * this.numero;
    },
    incrementar() {
      this.numero++;
    },
    decrementar() {
      this.numero--;
    },
  },
  computed: {
    calcularCuadradoComputado() {
      console.log("Entro a calcular computada");
      return this.numero * this.numero;
    },
  },
  //primera forma de declaracion de props
  //props:['encabezado','valor']
  //segunda forma de declaracion de props mas especializada
  //aqui se puede especificar el tipo de props
  //tambien se puede agregar validadores es que un criterio de validacion
  //para saber si es valido o no (sujeta a un valor true o false) 
  props:{
    encabezado:String,
    valor:Number,
    valor2:{
      type:Number,
      required:false,
      default:777,
      validator(value){
        //programo mi validacion bajo mi criterio y retorno true cuando es valido o falso cuando no es valido para MI
        return value<=777;
      }
    },
    esVerdad:{
      type:Boolean,
      required:true
    },
    arreglo:Array,
    fecha:Date,
    objetoPersona:Object,
  }
};
</script>

<style>
button {
  background: #64b687;
  border-radius: 5px;
  border: 1px solid white;
  cursor: pointer;
  margin: 0px 5px;
  padding: 5px 15px;
}

button:hover {
  background: #5aa67b;
}
</style>