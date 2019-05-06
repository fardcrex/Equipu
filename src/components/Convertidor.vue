<template>
    <div class="container-convert">
        <div class="container-convert__inputs">
            <div class="input-one">
                <input type="text" v-model="euro">
            </div>
            
            <div class="input-two">
                <input type="text" v-model="dolar" disabled>
            </div>
        </div>
        <div class="container-convert__boton">
            <button v-on:click="calcular">
                Convertir
            </button>
        </div>
    </div>
</template>
<script>
import axios from 'axios';
export default {
    
    data() {
        return {
            dolar:1,
            euro:1
        }
    },
    mounted(){
        setInterval(this.calcular(), 3000);
        this.calcular()
    },
    methods: {
            calcular:async function (){
              let res = await axios.get("http://data.fixer.io/api/latest?access_key=bccf73e34c3b762a1dfef225d7819280&symbols=USD");
              let rate = res.data.rates.USD
              this.dolar=  this.euro*rate
              this.dolar=  this.dolar.toFixed(4)
              }
        }
}
</script>
<style lang="scss" scoped>
    $breakpoint: 600px;
    .container-inputs{
            
        }
    .container-convert{ 
        width: 100%;
        max-width: 800px;
        background-color: aquamarine;
        display: grid;
        margin: auto;
        grid-template-rows: 25vh 20vh;
        justify-items: center;
        align-items: center;

        &__inputs{
            padding-top: 10vh;
            display:grid;
            width: 100%;
           
            @media screen and (min-width:$breakpoint){
                
                grid-template-columns: 1fr 1fr;
            }

        }
        &__boton{
               
            }
    }
input{
              height: 25px;
              width: 300px; 
              margin: 1rem;
     }
button{
               height: 25px;
              width: 300px; 
    }
</style>
