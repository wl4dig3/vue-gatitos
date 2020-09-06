vue <template>
  <div>
    <div class="container">
      <h3 class="text-center mt-5">Ingresa un mensaje en el campo de texto y presiona 'enter'</h3>
      <div class="input-wrap">
        <input class="mt-3" type="text" placeholder="mensaje" v-model="mensaje" />
        <p>
          Filtro
          <select v-model="filterSlected">
            <option disabled selected>Seleccione:</option>
            <option
              @click="filterSelected = item"
              v-for="item in filter"
              :key="item.id"
              :value="item"
            >{{item}}</option>
          </select>
        </p>

        <p>
          Color
          <select name="color" id></select>
        </p>
      </div>
      <!-- <button>buscar mininos</button> -->
    </div>
    <img :src="gatito" alt />
  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {
      filter: ["blur", "mono", "sepia", "negative", "paint", "pixel"],
      color: ["red", "green", "yellow", "blue", "black", "gray"],
      filterSelected: "Selecciona:",
      mensaje: "",
    };
  },
  computed: {
    gatito() {
      return `https://cataas.com/cat/says/${this.mensaje}?filter=${this.filterSelected}`;
    },
  },
};
</script>

<style lang="scss" scoped>
p {
  margin: 1rem 0;
}
</style>