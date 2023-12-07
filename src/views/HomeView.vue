<script setup>
import vendas from '../graficos/vendas.vue';
import maisvendidos from '../graficos/maisvendidos.vue';
import barraProgresso from '../components/barraProgresso.vue';
import { ref }  from 'vue'

const stepProgress = ref();

const data = {
  steps: ['Step 1', 'Step 2', 'Step 3'],

  // Step Atual !!!!!! IMPORTANTE !!!!!!
  currentStep: 3,

  activeColor: '#FFC107',
  passiveColor: '#C4C4C4',
}
</script>

<template>
  <div class="mainWrap">
    <div class="mainDiv" >
      <div class="graphDiv">
        <vendas class="graficoComp" />
      </div>
      <div class="graphDiv">
        <maisvendidos class="graficoComp" />
      </div>
        <barraProgresso :data="data" :ref="stepProgress" />
        <button @click="stepProgress.previousStep"> - </button>
        <button @click="stepProgress.nextStep"> + </button>
    </div>
  </div>
</template>

<style>
.graphDiv{
  width: 50%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 1%;
}
.graficoComp{
  width: 700px;
  height: 305px;
  background-color: #FFF2CC;
}
.mainWrap{
  width: 100%;
  height: 100%;
}
.mainDiv{
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>