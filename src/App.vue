vue <template>
  <div>
      <div>
        <input type="text" placeholder="mensaje" v-model="mensaje">
    <p>Filtro
      <select name="" id=""></select>
    </p>

    <p>
      Color
      <select name="color" id=""></select>
    </p>
    <button>buscar mininos</button>
      </div>
      <img :src="gatito"  alt="gatos">
  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {
      mensaje:""
    }
  },
  computed: {
    gatito(){
      return `https://cataas.com/cat/says/${this.mensaje}`;
    },
   
  },
}
</script>

<style lang="scss" scoped>

</style>