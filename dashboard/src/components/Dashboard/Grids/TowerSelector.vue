<template>
<div>
  <md-card class="tower-selector">
    <div class="name-container">
      <p class="name">{{ur.torres.length > 1 ? 'TORRES' : 'TORRE'}}</p>
    </div>
    <div class="contenedor">
        <div v-for="(torre, index) in ur.torres" :key="index" :class="selected(torre.numero)">
            <div @click="selectTower(torre.numero)">
                <md-button class="md-raised">{{torre.numero}}</md-button>
            </div>
        </div>
        
    </div>
  </md-card>
</div>
</template>

<script>
import data from "./ProvisionalData"; //Importar datos para probar front
export default {
  name: "TowerSelector",
  props: ["ur"], //Cambiar urPP a ur para despliegue real
  data: function() {
    return {
      //ur: null, //El despliegue real no tiene este atributo en el data
      boolean: true
    };
  },
  methods: {
    selectTower(numero) {
      this.$emit("select-tower", numero);
    },
    selected(numero) {
      let classObject = {};
      return classObject;
    }
  },
   mounted() {
    /* this.torres = this.ur; //set unidad to prop
    this.ur = data; */ //Reemplazar el prop 'ur' por una propiedad en el data, usando los datos importados
  }
};
</script>
<style scoped>
.name-container {
  font-weight: bold;
  font-size: 1.5rem;
  padding: 1rem 0;
  margin: none;
  background: rgb(77, 77, 77);
  color: white;
}

.name {
  margin: 0 0;
}

.md-card {
  display: inline-block;
  overflow: auto;
  border: 3px rgb(77, 77, 77) solid;
}

.contenedor {
  display: inline-block;
  max-height: calc(100vh - 300px);
  overflow-y: scroll;
}

.md-button {
  display: block;
  margin: 0;
  border-bottom: 3px rgb(77, 77, 77) solid;
}

.active-tower {
  background-color: aqua;
}

.md-button:last-child {
  border-bottom: none;
} 

.tower-selector{
  top:50%;
  transform: translate(0%,-50%);
}
</style>
