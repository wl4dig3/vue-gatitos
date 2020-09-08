vue <template>
<div>
    <h3 class="text-center mt-5">Ingresa un titulo para el gatito y presiona 'enter'</h3>
    <div class="container">
        <div class="input-wrap">
            <input class="mt-3" type="text" placeholder="titulo" v-model="mensaje" />
            <p>
                Filtro
                <select v-model="filterSelected">
                    <option disabled selected>Seleccione:</option>
                    <option @click="filterSelected = item" v-for="item in filter" :key="item.id" :value="item">{{item}}</option>
                </select>
            </p>

            <p>
                Color
                <select v-model="colorSelected">
                    <option disabled selected>Selecciona:</option>
                    <option @click="colorSelected = item" v-for="item in colors" :key="item.id" :value="item">{{item}}</option>
                </select>
            </p>
            <span></span>
            <span class="colorRound" :style="{ backgroundColor: this.colorSelected}">
                {{colorSelected}}
            </span>

            <p>
                Tamaño:
                <input type="number" v-model.number="size" min="1" />
            </p>
        </div>
        <!-- <button>buscar mininos</button> -->
    </div>
    <img :src="gatito" alt="tu gatito aqui" />
</div>
</template>

<script>
export default {
    name: "app",
    data() {
        return {
            filter: ["blur", "mono", "sepia", "negative", "paint", "pixel"],
            colors: ["red", "green", "yellow", "blue", "black", "gray"],
            filterSelected: "Selecciona un filtro:",
            colorSelected: " ",
            // size: null,
            mensaje: "",
        };
    },
    computed: {
        gatito() {
            return `https://cataas.com/cat/says/${this.mensaje}?filter=${this.filterSelected}&color=${this.colorSelected}&size=${this.size}`;
        },
    },
};
</script>

<style lang="scss" scoped>
.container {
    background-color: pink;
    margin: 2rem auto;
    padding: 1rem;
}

p {
    margin: 1rem 0;
}

img {
    border-radius: 50%;
    margin: 1rem 0 0 20rem;
}

colorRound {

    border: 1px solid;
    border-radius: 50%;
    width: 2rem;
    height: 2rem;
    margin-left: 2rem;
    background-color: black;
}
</style> 

// no funciona el input para el tamaño ni el round color :( sorry
