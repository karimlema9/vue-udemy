<template>
  <div>
    <div class="seccion">
      <div class="seccion">
        <div v-if="!pago && boletos == 0" class="mensaje informacion">Selecciona la menos un boleto.</div>
        <div
          v-else-if="!pago && boletos > 0"
          class="mensaje advertencia"
        >Recuerda completar tu compra.</div>
        <div v-else class="mensaje exito">¡Bienvenido!</div>
        <div class="atributo">
          <span>Asientos</span>
        </div>
        <div class="atributo">
          <button @click="seleccionar(asiento, index)" v-for="(asiento, index) in asientos" :key="index">{{ asiento }}</button>
        </div>
      </div>
      <div class="atributo">
        <span>Boletos</span>
      </div>
      <div class="atributo">
        <span class="boletos">{{boletos}}</span>
      </div>
      <div v-show="boletos > 0" class="atributo">
        <span>Total: ${{ total }}</span>
      </div>
      <div class="atributo">
          <button class="seleccion" @click="remover(asiento, index)" v-for="(asiento, index) in seleccionados" :key="index">{{ asiento }}</button>
        </div>
      <div v-if="!pago && boletos > 0" class="atributo">
        <button @click="pago = true">Pagar</button>
      </div>
      <div v-if="pago" class="atributo">
        <button @click="reiniciar">Reiniciar</button>
      </div>
      <div class="atributo">
        <span class="comision" :class="classeComision">${{comision}}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      comision: 0,
      classeComision: "neutro",
      pago: false,
      asientos: [
        'A1','A2','A3','A4','A5',
        'B1','B2','B3','B4','B5'
      ],
      seleccionados: []
    };
  },
  computed: {
    boletos() {
      return this.seleccionados.length
    },
    total() {
      return this.boletos * 100;
    }
  },
  methods: {
    seleccionar(asiento, index) {
      this.asientos.splice(index, 1)
      this.seleccionados.push(asiento)
      this.seleccionados.sort()
    },
    remover(asiento, index) {
      this.seleccionados.splice(index, 1)
      this.asientos.push(asiento)
      this.asientos.sort()
    },
    reiniciar() {
      this.pago = false;
      this.asientos.push(...this.seleccionados)
      this.asientos.sort()
      this.seleccionados = []
      this.comision = 0;
    }
  },
  watch: {
    boletos(newValue, oldValue) {
      if (newValue > oldValue) {
        this.comision += 10;
        this.classeComision = "incremento";
      } else {
        this.comision -= 15;
        this.classeComision = "decremento";
      }

      if (this.comision < 0) {
        this.comision = 0;
        this.classeComision = "neutro";
      }
    }
  }
};
</script>

<style>
.boletos {
  font-size: 4rem;
  font-weight: bold;
}

.comision {
  font-size: 3.2rem;
}

.neutro {
  color: black;
}

.incremento {
  color: green;
}

.decremento {
  color: red;
}

.mensaje {
  border-radius: 5px;
  border-width: 4px;
  border-style: dashed;
  padding: 10px;
  font-size: 2.1rem;
  font-weight: bold;
}

.informacion {
  border-color: blue;
}

.advertencia {
  border-color: orange;
}

.exito {
  border-color: green;
}

.seleccion {
  background-color: #1dca1d;
}
</style>