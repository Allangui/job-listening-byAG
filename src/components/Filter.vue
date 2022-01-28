<script>
export default {
    name:"Filtre",
    props:["clearFilter","removeFilter","selected"]
}
</script>
<template>
    <div class="filter">
        <ul class="filter-content" >
            <li class="itemSelected" v-for="item in selected" :key="item" @click="removeFilter(item)">{{ item }}</li>
        </ul>
        <button class="clear" @click="clearFilter()">Clear</button>
    </div>
</template>
 
<style lang="scss">

.filter{
    background:white;
    height:auto;
    width:85vw;
    padding:15px 20px;
    position: relative;
    margin: 100px auto 0;
    border-radius: 10px;
    max-width: 325px;
    z-index: 10;
    display:flex;
    justify-content: space-between;
    align-items: center;
    }
    .filter-content{
    flex-grow: 10;
    display:flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: flex-start;
    align-items: center;
    margin-top:10px;
    }
    .itemSelected{
    color:hsl(180, 29%, 50%);
    padding:7px 5px 6px;
    margin: 8px 17px 8px 0;
    background-color:hsl(180, 31%, 95%);
    border-radius: 5px;
    font-size: .8rem;
    cursor: pointer;
    }
    .clear{
    flex-grow: 1;
    border:none;
    background-color:transparent;
    font-weight: 700;
    color:hsl(180, 7%, 59%);
    font-size: .8rem;
    width:auto;
    height:auto;
    font-family: 'Spartan', sans-serif;
    cursor: pointer;
    }
</style>
