<template>
  <div class="w-full h-full flex justify-center items-center">
    <div class="grid grid-rows-5 gap-4 w-full bg-base-200 p-5 rounded-md">
      <div class="row-span-1 flex flex-col justify-end items-center mb-4">
        <!-- Dropdown for selecting column -->
        <details class="dropdown">
          <summary class="btn m-1">{{ coluna ? coluna : "Selecionar Coluna" }}</summary>
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
      <div v-for="(letter, index) in ['B', 'I', 'N', 'G', 'O']" :key="index" class="flex items-center">
        <div class="flex items-center justify-center w-16 h-16 text-7xl font-bold">{{ letter }}</div>
        <div class="flex space-x-2">
          <input
            v-for="i in getColumn(letter)"
            :key="i"
            type="number"
            min="0"
            max="99"
            :class="html.input"
          />
        </div>
      </div>
    </div>
  </div>

  <footer class="footer sm:footer-horizontal bg-neutral text-neutral-content p-7">
  <aside>
    <img src="/GGD-LogoSFundo.png" class="h-20"></img>
    <p>
      © 2025 Guerra Game Design
    </p>
  </aside>
  <nav>
  </nav>
</footer>

</template>

<script>
export default {
  data() {
    return {
      b: 1,
      i: 1,
      n: 1,
      g: 1,
      o: 1,
      coluna: null,
      html: {
        input: "input md:w-28 md:h-28 w-14 h-14 text-2xl md:text-7xl font-bold text-center",
      },
    };
  },
  methods: {
    incrementarColuna() {
      console.log(this.coluna);
      this.coluna == "b"
        ? this.b++
        : this.coluna == "i"
        ? this.i++
        : this.coluna == "n"
        ? this.n++
        : this.coluna == "g"
        ? this.g++
        : this.coluna == "o"
        ? this.o++
        : "";
      this.coluna = null;
    },
    getColumn(letter) {
      return this[letter.toLowerCase()];
    },
  },
};
</script>

<style>
input[type="number"]::-webkit-inner-spin-button,
input[type="number"]::-webkit-outer-spin-button {
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
  margin: 0;
}

.flex.items-center.justify-center.w-16.h-16 {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 4rem; /* Adjust width */
  height: 4rem; /* Adjust height */
}
</style>
