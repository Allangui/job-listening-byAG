<template>

  <div id="app">
    <header></header>
    <Filtre
    v-if="selected.length>0"
    :selected = "selected"
    :clearFilter = "clearFilter"
    :removeFilter = "removeFilter"
    />
    <Card
    v-for="data in datas"
    :getSelected="getSelected"
    :pushFilter="pushFilter"
    :company="data.company"
    :logo="data.logo"
    :news="data.new"
    :featured="data.featured"
    :position="data.position"
    :role="data.role"
    :level="data.level"
    :postedAt="data.postedAt"
    :contract="data.contract"
    :location="data.location"
    :languages="data.languages"
    :tools="data.tools"
    :key="data.id"
    class="mainCard"
    />
  </div>
</template>

<script>
import Card from './components/Card.vue';
import datas from '../data.json';
import Filtre from'./components/Filter.vue';

export default {
  name: 'app',
  data(){
    return{
      datas: datas,
      selected:[],
    }
  },
  components: {
    Card,
    Filtre,
  },
  methods:{
    pushFilter(value){
      if(this.selected.includes(value)){
      alert('Déjà selectionné')
      }else {
        return this.selected.push(value)
      }
    },
    clearFilter(){
      return this.selected.splice(0, this.selected.length)
    },
    removeFilter(value){
      const index = this.selected.indexOf(value)
      return this.selected.splice(index,1);
    },
    getSelected(role,level,languages,tools){
      let myArray = [role,level].concat(languages,tools)
      let value = true
      for(let i = 0 ; i< this.selected.length ; i++){
        if( this.selected.length === 0 ){
         value = true
       } else if(myArray.includes(this.selected[i])) {
         value = true
      }else {
         value = false
       }
      }  
      
       return value
    },
    forArray(array){
      for( let i=0 ; i< array.length ; i++){
          return array[i]
      }
    }
  },
  mounted(){
        this.clearFilter()
        
    }
}
</script>

<style lang="scss" >
@import "../libs/reset.scss" ;

body{
  margin-top:100px;
  background-color: hsl(180, 52%, 96%);
}
header{
  height:150px;
  width:100%;
  position:absolute;
  z-index:1;
  top:0;
  left:0;
  background: url("../images/bg-header-mobile.svg") top center /cover no-repeat;
  background-color: hsl(180, 29%, 50%);
}

#app {
  font-family: 'Spartan', sans-serif;
  font-size: .9rem;
  font-weight: 700;
  text-align: left;
  color: #2c3e50;
}
</style>
