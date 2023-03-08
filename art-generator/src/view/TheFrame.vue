<script setup lang="ts">
import Circle from "./../components/Circle.vue"
import Edge from "./../components/Edge.vue"
import {ref,computed, onMounted} from 'vue'

defineProps<{
  msg: string
}>()

// return random rgb Color
function rColor(){

  // return number between 0 and 256
  function n0_256(){
    return Math.floor(Math.random() * 256);
  };
  const opacity = 1;
  
  return 'rgba('+ n0_256() + ',' + n0_256() + ',' + n0_256() + ',' + opacity + ')';
}

// static parameter  
const maxDiffColors = 7;

// list of 7 random color
var sevenColor = new Array;

function fillSevenColors(){
for (let i = 0; i < maxDiffColors; i++){
  //rgba(252,176,69,1)
  const randColor = rColor();
  sevenColor.push(randColor);
}}

var firstColor = ref("white");
var secondColor = ref("white");
var thirdColor = ref("white");

var firstG = ref(0);
var secondG  = ref(50);
var thirdG  = ref(100);

function towColorsBackground() {
  firstG.value = Math.floor(Math.random() * 98);
  //Obtenir un entier aléatoire dans un intervalle fermé
  secondG.value = Math.floor(Math.random() * (98 - firstG.value+1)) + firstG.value+1;
  thirdG.value = Math.floor(Math.random() * (99 - secondG.value)) + secondG.value+1;


  firstColor.value = sevenColor.pop(); 
  secondColor.value = sevenColor.pop(); 
  if(Math.random() > 0.5){
    thirdColor.value = firstColor.value; 
  }
  else {
    thirdColor.value = secondColor.value;
  }
  //reinitaliser la liste
  fillSevenColors();
}

</script>

<template>
  <div class="container flex">
    {{ firstColor }}
    {{ secondColor }}
    {{ thirdColor }}
    {{ firstG }} {{secondG}} {{thirdG }}
  <h1>Art Generator</h1>
  <div class="frame background">
 
    <!--Circle></Circle>
    <Edge ></Edge-->
  </div>
  <button @click="towColorsBackground()">Generate</button>
</div>
</template>

<style scoped>

.frame {
position: relative;
border: 1px black solid;
width: 400px;
height: 600px;
overflow: hidden;
}

.background {
  background: v-bind('firstColor');
background: linear-gradient(90deg, 
v-bind('firstColor') 0%, 
v-bind('secondColor') 50%, 
v-bind('thirdColor') 100%);

/*background: rgb(131,58,180);
background: radial-gradient(circle, 
rgba(131,58,180,1) 0%, 
rgba(253,29,29,1) 50%, 
rgba(252,176,69,1) 100%);*/
}

h1 {
  text-align: center;
}

button {
  margin-top: 20px;
  height: 50px;
  cursor: pointer;
}

/*.container {}*/

.flex {
  display: flex;
  flex-direction: column;
  justify-content: center;
}

@media (min-width: 1024px) {
}
</style>
