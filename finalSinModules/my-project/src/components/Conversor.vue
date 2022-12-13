<template>

  <section class="src-componentes-estructura">
    <div class="jumbotron">
      <h2>Conversor de moneda</h2>
      <hr>
      <hr>
      <br>
      
     

        <div class="form-group">
        <label for="pesos">Ingrese monto ARS$</label>
        <input type="number" id="pesos" class="form-control" v-model.number="formData.pesos" @input="formDirty.pesos = true">

        <!-- cartel validación -->
        <div v-if="!formData.pesos && formDirty.pesos" class="alert alert-danger mt-1">
          Campo requerido
        </div>

      </div>



        <div class="form-group">
        <label for="dolar">Valor del dolar USD$</label>
        <input type="number" id="dolar" class="form-control" v-model.number="formData.dolar" @input="formDirty.dolar = true">

        <!-- cartel validación -->
        <div v-if="!formData.dolar && formDirty.dolar" class="alert alert-danger mt-1">
          Campo requerido
        </div>

      </div>


      <div v-if="!formData.pesos && !formData.dolar" class="alert alert-danger mt-1">
        <h4 class="alert alert-info">
          Valor convertido de Pesos Argentinos a Dólar: 
          </h4>
        </div>
        <div class="div" v-else>
          <h4 class="alert alert-info">
              Valor convertido de Pesos Argentinos a Dólar: {{convertirMoneda}}
          </h4>
        </div>

      <br>
      <br>
      <br>
      <br>
    
      <br>
    

      


        </div>
        
      <h2>Respuestas</h2>
      
      <br/>
      <table class="table table">
          <tr>
            <th>Numero de pregunta</th>
            <th>Respuesta</th>
          </tr>
          <tr v-for="(pregunta, index) in preguntas"
              :key="index">
            <td>{{ pregunta.numero }}</td>
            <td>{{ pregunta.respuestas }}</td>
          </tr>
          
        </table>
      <br>
   

  </section>

</template>

<script>

  export default  {
    name: 'src-componentes-estructura',
    props: [],
    mounted () {

    },
    data () {
      return {
        formData: this.getInitialData(),
        formDirty: this.getInitialData(),
        preguntas : [
          {numero : 1, respuestas : ['c']},
          {numero : 2, respuestas : ['b']},
          {numero : 3, respuestas : ['c']},
          {numero : 4, respuestas : ['a']},
          {numero : 5, respuestas : ['b']},
        ]

        
      }
    },
    methods: {
        getInitialData() {
      return {
        pesos: null,
        dolar: null,
        
      }
    },

    },
    computed: {
      convertirMoneda(){
            let valor=this.formData.pesos/this.formData.dolar
            {
              return valor.toFixed(2) 
            }
            
        }
  }
        
    
}


</script>

<style scoped lang="css">
  .src-componentes-estructura {
    
  }

  .jumbotron {
    background-color: rgb(0, 0, 0);
    color: white;
  }

  hr {
    background-color: #bbb;
  }
</style>
