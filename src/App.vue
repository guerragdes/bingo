<template>
  <div class="w-full h-full flex justify-center items-center">
    <div class="grid grid-cols-5 gap-1 md:w-6/12 bg-base-200 p-5 rounded-md">
      <div class="col-span-5 flex justify-end items-center">
        <!-- Open the modal using ID.showModal() method -->
        <details class="dropdown">
              <summary class="btn m-1">{{ coluna? coluna: "Selecionar Coluna" }}</summary>
              <ul class="menu dropdown-content bg-base-100 rounded-box z-1 w-52 p-2 shadow-sm">
                <li @click="coluna='b'"><a>B</a></li>
                <li @click="coluna='i'"><a>I</a></li>
                <li @click="coluna='n'"><a>N</a></li>
                <li @click="coluna='g'"><a>G</a></li>
                <li @click="coluna='o'"><a>O</a></li>
              </ul>
            </details>
        <button class="btn" @click="incrementarColuna">Adicionar Número</button>
        
      </div>
      <div :class="html.div">
        B
        <input type="number" min="0" max="99" :class="html.input" v-for="i in b" />
      </div>
      <div :class="html.div">
        I
        <input type="number" min="0" max="99" :class="html.input" v-for="i in i" />
      </div>
      <div :class="html.div">
        N
        <input type="number" min="0" max="99" :class="html.input" v-for="i in n"/>
      </div>
      <div :class="html.div">
        G
        <input type="number" min="0" max="99" :class="html.input" v-for="i in g"/>
      </div>
      <div :class="html.div">
        O
        <input type="number" min="0" max="99" :class="html.input" v-for="i in o"/>
      </div>
    </div>
  </div>


</template>

<script>
  export default {
    data() {
      return {
        b:1, i:1, n:1, g:1, o:1,
        coluna:null,
        html: {
          div: "text-center text-5xl font-bold flex flex-wrap flex-col items-center space-y-2",
          input: "input md:w-20 md:h-20 w-14 h-14 text-5xl font-bold text-center",
          type: "number",
          min: "0",
          max: "99",

        }
      }
    } ,
    methods: {
      incrementarColuna() {
        console.log(this.coluna)
        this.coluna=="b"? this.b++ : 
        this.coluna=="i"? this.i++ :
        this.coluna=="n"? this.n++ :
        this.coluna=="g"? this.g++ :
        this.coluna=="o"? this.o++ : "";
        this.coluna=null
      }
    }
  }
</script>

<style>
  input[type=number]::-webkit-inner-spin-button, 
    input[type=number]::-webkit-outer-spin-button { 
        -webkit-appearance: none;
        -moz-appearance: none;
        appearance: none;
        margin: 0; 
    }
</style>