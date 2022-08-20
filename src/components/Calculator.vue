<template>
    <div class="calc">
    
        <div class= "dsipaly">{{resultado || 0}}</div>
        <div class="btn clear " @click="clean ">C</div>
        <div class="btn operador" @click="per">%</div>
        <div class="btn" @click="append(7)">7</div>
        <div class="btn" @click="append(8)">8</div>
        <div class="btn" @click="append(9)">9</div>
        <div class="btn operador"  @click="divide">/</div>
        <div class="btn" @click="append(4)">4</div>
        <div class="btn" @click="append(5)">5</div>
        <div class="btn" @click="append(6)">6</div>
        <div class="btn operador"  @click="multiply">X</div>
        <div class="btn" @click="append(1)">1</div>
        <div class="btn" @click="append(2)">2</div>
        <div class="btn" @click="append(3)">3</div>
        <div class="btn operador"  @click="resta">-</div>
        <div class="btn" @click="append(0)">0</div>
        <div class="btn" @click="dot">.</div>
        <div class="btn operador" @click="igual">=</div>
        <div class="btn operador" @click="suma">+</div>
    

    </div>


</template>
<script>
export default{
    data(){
        return {
            resultado: '',
            prev: null,
            operador: null,
            operadorClick: false
        }
    },
    methods: {
        clear(){
            this.resultado = '';
        },
        per(){
            this.resultado = parseFloat(this.resultado)/100;
        },
        append(number){
            if(this.operadorClick){
                this.resultado = '';
                this.operadorClick = false;
            }
            this.resultado = this.resultado+number;
        },
        dot(){
            if(this.resultado.indexOf('.') === -1){
                this.append('.');
            }
        },
        divide(){
            this.operador = (a,b) => b/a;
            this.setPrev();
            },
        multiply(){
            this.operador = (a,b) => b*a;
            this.setPrev();
            },
        resta(){
            this.operador = (a,b) => b-a;
            this.setPrev();
            },
        suma(){
            this.operador = (a,b) => b+a;
            this.setPrev();
            },
            igual(){
                this.igual = this.operador(
                    parseFloat(this.resultado),
                    parseFloat(this.prev)
                );
                this.prev=null;
            },
            setPrev(){
                this.prev= this.resultado;
                this.operadorClick = true;
            }
        }


    }

    
</script>


<style>
 *{
    background: #111;
 }
 .calc{
    width: 400px;
    margin: 0 auto;
    font-size: 40px;
    display: grid;
    grid-auto-rows: minmax(auto,auto);
    border: 20px groove #999;
 }
  .display{
    grid-column: 1/5;
    background: #333;
    color: #fff
    padding

  }
  .clear{
    grid-column: 1/4;
  }
  .btn{
    padding: 10px;
    background: linear-gradient(#fafafa,lightgrey);
    border: 1px solid #999;
    cursor: pointer;
  }
  .btn:activate{
    background: #777;
    color: #fff;
  }
  .operador{
    color: red;
  }




</style>