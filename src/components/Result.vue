<template>
  <div class="r-container fade-in">
    <h1>Results: </h1>
    <p v-if="total < 2 && total !== 0">You answered <span>{{ total }} question</span> correctly.</p>
    <p v-else>You answered <span>{{ total }} questions</span> correctly.</p>
    <div v-for="result in results" :key="result" v-show="result.correct === total" class="message">{{result.text}}</div>

    <h4>Credits:</h4>
    <p>Created by William Cazes</p>
  </div>
</template>

<script>
export default {
    props:["total", "results"]

}
</script>

<style scoped>
h1,h4{
    margin-top:30px
}
.r-container{
    padding:15px;
    margin:3px 0px;
    background: #efefef;
    border-bottom:3px solid #dfdfdf;
}
span{
    font-weight: 900;
}
p{
    margin:5px 0px;
}
.message{
    margin:40px 0px;
    font-weight: 900;
    text-align: center;
}

</style>