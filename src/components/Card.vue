<script>
export default {
    name:"Card",
    props:["getSelected","pushFilter","id","company","logo","news","featured","position","role","level","postedAt","contract","location","languages","tools"],
    
}
</script>
<template>
    <div class="card" v-if="getSelected(role,level,languages,tools)" >
        <img class="logo" :src="require(`../../images/${logo}`)" alt="logo" />
        <div class="company"> {{ company }} <span class="new" v-if="news">NEW!</span> <span class="featured" v-if="featured">FEATURED</span></div>
        <h1> {{ position }}</h1>
        <div class="description">
            <span class="postedAt">{{ postedAt }}</span>
            <span class="contract">{{ contract }}</span>
            <span class="location">{{ location }}</span>
        </div>
        <ul class="keywords">
            <li class="role keyword" @click="pushFilter(role)"> {{ role }} </li>
            <li class="level keyword" @click="pushFilter(level)"> {{ level }}</li>
            <li class="languages keyword" v-for="item in languages" :key="item" @click="pushFilter(item)"> {{ item }} </li>
            <li class="tools keyword" v-for="item in tools" :key="item" @click="pushFilter(item)"> {{ item }} </li>
        </ul>
    </div>
</template>

<style lang="scss" >
.card{
    background:white;
    height:auto;
    width:85vw;
    position:relative;
    padding:30px 20px 15px;
    margin: 50px auto ;
    border-radius: 10px;
    max-width: 325px;
    z-index:9;

}
.logo{
    width:50px;
    height:50px;
    position :absolute;
    top:0;
    transform: translateY(-50%);
    left:20px;
}
.company{
    color:hsl(180, 29%, 50%);
    margin:10px 0;
    line-height: 1.5rem;
    display: inline-block;
}
.new{
background-color:hsl(180, 29%, 50%) ;
margin-left:10px;
margin-right:5px;
}
.featured{
background-color:hsl(180, 14%, 20%) ;
}
.new, .featured{
color:white;
padding:7px 8px 6px;
border-radius: 30px;
font-size: .7rem;
letter-spacing: .01rem;

}
h1{
    font-weight:700;
    font-size: .9rem;
    margin:0;
}
.description{
    font-weight: 500;
    color:hsl(180, 8%, 52%);
    font-size: .7rem;
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    align-items: center;
    padding: 10px 0;
    border-bottom: solid 1px rgba(131, 131, 131, 0.5);
    span{
        display: inline-block;
        &:before{
            content:'•';
            width: auto;
            height: auto;
            vertical-align: middle;
            font-size:1.2rem;
            opacity:.5;
            margin: 0 5px;
        }

        &:first-child{
            &:before{
            content:'';
            margin:0;
            }
        }
    }
    
}
.keywords{
    display: flex;
    flex-wrap: wrap;
    justify-content: flex-start;
    align-items: center;
    margin-top:10px;
    .keyword{
        color:hsl(180, 29%, 50%);
        padding:7px 5px 6px;
        margin: 8px 17px 8px 0;
        background-color:hsl(180, 31%, 95%);
        border-radius: 5px;
        font-size: .8rem;
        cursor: pointer;
    }
}
</style>