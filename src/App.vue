<script setup>
  import { computed, ref} from 'vue'

  const count = ref(0)

  const numeros = ref([])

  const agregar = () => {
    numeros.value.push(count.value)
  }

  const numeroRepetido = computed(() => {
    const numberFind = numeros.value.find(numero => numero === count.value)
    if(numberFind === 0) return true
    return numberFind ? true : false
  })

  const aumentar = () => {
    count.value++
  }

  const disminuir = () => {
    count.value--
  }

  const resetear = () => {
    count.value = 0
  }
  
  const classCounter = computed(() => {
    if(count.value === 0){
      return 'neutro'
    }
    if(count.value > 0){
      return 'positive'
    }
    if(count.value < 0) {
      return 'negative'
    }
  })
</script>


<template>
    <div class="container-1">
      <h1 :class="classCounter"> {{ count }}</h1>
      <div class="botones">
        <button @click="disminuir">Disminuye</button>
        <button @click="aumentar">Aumenta</button>
        <button @click="resetear">Resetea</button>
        <button @click="agregar" :disabled="numeroRepetido">Agregar</button>
      </div>
      <h1> {{ numeros }}</h1>    
    </div>


</template>

<style scoped>
.container-1{
  text-align: center;
  font-size: 20px;
  background-color: whitesmoke;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 2px 5px 10px rgba(0, 0, 0, 0.8);
}

.positive{
  color: green;
}

.negative{
  color: red;
}

.neutro{
  color: black;
}

button {
  width: 200px;
  padding: 20px;
  margin: 20px;
  background-color:cadetblue;
  color: white;
  border-radius: 10px;
  border: none;
  font-size: 20px;
  box-shadow: 2px 5px 10px rgba(0, 0, 0, 0.8);
}

button:hover{
  background-color: rgb(64, 100, 102);
}

button:disabled{
  background-color: gray;
}

</style>