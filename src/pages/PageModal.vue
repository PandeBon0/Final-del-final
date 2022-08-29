<template>
  <div class="modal-overlay" v-show="open" >
    <div class="modal-content">
      <!-- <slot></slot>
      <hr> -->
      <span @click="$emit('close')" class="close-button topright">&times;</span>


      <div class="text-left">
        <h2 class="text-xl font-bold text-center">Crear producto</h2>
        <br>
        <h2 class="text-lg	font-semibold">Informacion del producto</h2>
        <br>

        <form @submit="submitForm">
          <!--INICIO FORM-->
          <div class="flex flex-col">
            <label for="descripcion" class="">Descripcion</label>
            <select id="categoria" class="border rounded border-slate-300 h-15 text-slate-400">
              <option value="">Seleccione una categoria</option>
              <option value="alimentos">Alimentos</option>
              <option value="tecnologia">Tecnologia</option>
              <option value="vestimenta">Vestimenta</option>
            </select>
          </div>

          <br>
          <div class="flex flex-col">
            <label for="titulo" class="">Titulo</label>
            <input type="text" id="titulo" class="border rounded border-slate-300 h-15" v-model="formValues.titulo"
              required maxlength="40">
          </div>
          <br>
          <div class="flex flex-col">
            <label for="descripcion" class="">Descripcion</label>
            <input type="text" id="descripcion" class="border rounded border-slate-300 h-15"
              v-model="formValues.descripcion" maxlength="100">
          </div>
          <br>
          <div class="flex flex-col">
            <label for="descripcionPro" class="">Descripcion pro</label>
            <textarea type="text" id="descripcionPro" class="border rounded border-slate-300 h-15"
              v-model="formValues.descripcionPro" maxlength="1000"></textarea>
          </div>
          <br>
          <h2>Variantes</h2>
          <!--VARIANTES SELECTORES-->
          <br>
          <div class="grid grid-cols-2 border border-transparent border-b-slate-400">
            <label for="talla" class="">Talla</label>
            <select id="talla" v-model="formValues.talla">
              <!--como espaciar flex items y que funcione-->
              <option value=""> </option>
              <option value="s">S</option>
              <option value="m">M</option>
              <option value="l">L</option>
            </select>
          </div>
          <br>
          <div class="grid   grid-cols-2 border border-transparent border-b-slate-400">
            <label for="color" class="">Color</label>
            <select id="color" v-model="formValues.color">
              <!--como espaciar flex items y que funcione-->
              <option value=""></option>
              <option value="rojo">Rojo</option>
              <option value="amarillo">Amarillo</option>
              <option value="verde">Verde</option>
              <option value="azul">Azul</option>
            </select>
          </div>
          <br>
          <div class="grid   grid-cols-2 border border-transparent border-b-slate-400">
            <label for="sabor" class="">Sabor</label>
            <select id="sabor" v-model="formValues.sabor">
              <!--como espaciar flex items y que funcione-->
              <option value=""></option>
              <option value="dulce">Dulce</option>
              <option value="salado">Salado</option>
              <option value="acido">Acido</option>
            </select>
          </div>

          <div class="flex flex-row items-center ml-20">
            <img class="bg-white-500 p-6  mx-10 h-13" src="@/assets/PopupImages/mas.png">
            <h2 class="text-sky-400	">Agregar grupo de Toppings</h2>
          </div>

          <h2 class="text-lg	font-semibold">Precio y disponibilidad</h2>
          <br>

          <div class="flex flex-row">
            <div class="flex flex-col">
              <label for="cantidad" class="">Cantidad</label>
              <input type="text" v-model="formValues.cantidad" id="cantidad"
                class="border rounded border-slate-300 h-15 mr-2 my-0.5  gap-4" required step="1" min="0" max="1000000"
                onkeypress="if ( isNaN( String.fromCharCode(event.keyCode) )) return false;">
            </div>
            <div class="flex flex-col">
              <label for="sku" class="">SKU</label>
              <input type="text" v-model="formValues.sku" id="sku"
                class="border rounded border-slate-300 h-15 mr-2 my-0.5  gap-4" required maxlength="20"
                onkeypress="if ( isNaN( String.fromCharCode(event.keyCode) )) return false;">
            </div>
          </div>

          <div class="flex flex-row">
            <div class="flex flex-col">
              <label for="moneda" class="">Moneda</label>
              <select id="moneda" v-model="formValues.moneda"
                class="border rounded border-slate-300 h-19 text-slate-400 mr-9 my-0.5 ">
                <!--como espaciar flex items y que funcione-->
                <option value="">Seleccione moneda</option>
                <option value="peso">Pesos Colombianos</option>
                <option value="dolar">Dolares</option>
                <option value="euro">Euros</option>
              </select>
            </div>
            <div class="flex flex-col">
              <label for="precio" class="">Precio</label>
              <input type="text" v-model="formValues.precio" id="precio"
                class="border rounded border-slate-300 h-15  mr-2 my-0.5  gap-4" required step="50" min="0"
                max="1000000000" onkeypress="if ( isNaN( String.fromCharCode(event.keyCode) )) return false;">
            </div>
          </div>
          <br>
          <h2 class="text-lg	font-semibold">Precio y disponibilidad</h2>

          <div class="flex flex-row">


            <div class="flex flex-col">
              <h2 class="semibold">Peso</h2>
              <div class="flex flex-row">
                <input type="text" v-model="formValues.peso" id="peso"
                  class="border rounded border-slate-300 h-15 my-0.5 mr-2 gap-4" required step="1" min="0"
                  max="10000000" onkeypress="if ( isNaN( String.fromCharCode(event.keyCode) )) return false;">
                <h2 class="mx-1">Grs</h2>
              </div>

            </div>

            <div class="flex flex-col">
              <h2 class="semibold">Alto</h2>
              <div class="flex flex-row">
                <input type="text" v-model="formValues.alto" id="alto"
                  class="border rounded border-slate-300 h-15 my-0.5 mr-2 gap-4" step="10" min="0" max="1000000"
                  onkeypress="if ( isNaN( String.fromCharCode(event.keyCode) )) return false;">
                <h2 class="mx-1">cm</h2>
              </div>
            </div>

            <div class="flex flex-col">
              <h2 class="semibold">Ancho</h2>
              <div class="flex flex-row">
                <input type="text" v-model="formValues.ancho" id="ancho"
                  class="border rounded border-slate-300 h-15 my-0.5 mr-2 gap-4" required step="10" min="0"
                  max="1000000" onkeypress="if ( isNaN( String.fromCharCode(event.keyCode) )) return false;">
                <h2 class="mx-1">cm</h2>
              </div>
            </div>

            <div class="flex flex-col">
              <h2 class="semibold">Profundo</h2>
              <div class="flex flex-row">
                <input type="text" v-model="formValues.profundo" id="profundo"
                  class="border rounded border-slate-300 h-15 my-0.5 mr-2 gap-4" required step="10" min="0"
                  max="1000000" onkeypress="if ( isNaN( String.fromCharCode(event.keyCode) )) return false;">
                <h2 class="mx-1">cm</h2>
              </div>
            </div>
            <br>
          </div>
          <br>
          <h2 class="text-lg	font-semibold">Fotos del producto</h2>
          <h2 class="ml-10"> <b>Importante: </b>Las imagenes son el componente mas importante de <br>
            un buen e-commerce. Por favor cargue imagenes de buena calidad <br>y tamaño. Le recomendamos usar estandares
            de
            proporcion 4:3 y <br>color de fondo unificado
          </h2>
          <br>
          <label for="avatar">Escoja una imagen: </label>

          <div class="grid grid-cols-2 items-left">
            <input type="file" id="avatar" name="avatar" accept="image/png, image/jpeg">
            <button class="font-semibold border rounded border-slate-300 p-2 bg-sky-500 w-20 text-white"
              @click="demoVisibility(), changeNumericProgress(), changeProgressBar(), cleanForm()">Submit</button>
          </div>


        </form>
        <!--FIN FORM-->

      </div>


      <button @click="$emit('close')">Close</button>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'PageModal',
    visibility: 'invisible',
    // emits: ["close"],
    props:{
      open:{
        type:Boolean,
        required:true
      }
    },
    data() {
    return {
      fechas:'',
      numericProgress:'(2/8)',
      formValues:{
        titulo:'',
        descripcion:'',
        descripcionPro:'',
        categoria:'',
        talla:'',
        color:'',
        sabor:'',
        precio:'' ,
        moneda:'' ,
        cantidad:'',
        sku:'' ,
        peso:'',
        alto:'',
        ancho:'',
        profundo:'',
      }
    };
  },
  
  methods:{
    submitForm(){
      event.preventDefault()
      console.log('Form values', this.formValues)
    },
    demoVisibility() {
      document.getElementById("chulito").style.visibility = "visible";
    },
    changeNumericProgress(){
      this.numericProgress='(3/8)'
    },
    changeProgressBar() {
      document.getElementById("progressBar").style.width = '42%';
    },
    cleanForm(){
        this.formValues.titulo='',
        this.formValues.descripcion='',
        this.formValues.descripcionPro='',
        this.formValues.categoria='',
        this.formValues.talla='',
        this.formValues.color='',
        this.formValues.sabor='',
        this.formValues.precio='' ,
        this.formValues.moneda='' ,
        this.formValues.cantidad='' ,
        this.formValues.sku='' ,
        this.formValues.peso='',
        this.formValues.alto='',
        this.formValues.ancho='',
        this.formValues.profundo=''
    },
  },
}
</script>

<style scoped>
.modal-overlay {
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  display: grid;
  justify-content: center;
  align-items: center;
  background-color: rgba(0, 0, 0, 0.3);
}

.modal-content {
  /* font-family: "Fondamento", cursive; */
  padding: 20px;
  background: #fff;
  border-radius: 2px;
  display: inline-block;
  min-height: 300px;
  margin: 1rem;
  position: relative;
  min-width: 300px;
  box-shadow: 0 3px 6px rgba(0, 0, 0, 0.16), 0 3px 6px rgba(0, 0, 0, 0.23);
  justify-self: center;
}

::-webkit-scrollbar {
  width: 10px;
}

/* Track */
::-webkit-scrollbar-track {
  background: #f1f1f1; 
}
 
/* Handle */
::-webkit-scrollbar-thumb {
  background: #888; 
}

/* Handle on hover */
::-webkit-scrollbar-thumb:hover {
  background: #555; 
}

.close-button {
  border: none;
  display: inline-block;
  padding: 8px 16px;
  vertical-align: middle;
  overflow: hidden;
  text-decoration: none;
  color: inherit;
  background-color: inherit;
  text-align: center;
  cursor: pointer;
  white-space: nowrap
}

.topright {
  position: absolute;
  right: 0;
  top: 0
}
</style>