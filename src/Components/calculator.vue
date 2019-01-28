<template>
  <div class="calculator">
      <div class="display">{{current || '0'}} </div>
      <div @click="clear" class="btn" >C</div>
      <div @click="sign" class="btn">+/-</div>
      <div @click="percent" class="btn">%</div>
      <div @click="divide" class="btn operator">/</div>
      <div @click="number(7)" class="btn">7</div>
      <div @click="number(8)" class="btn">8</div>
      <div @click="number(9)" class="btn">9</div>
      <div @click="multiply" class="btn operator">*</div>
      <div @click="number(4)" class="btn">4</div>
      <div @click="number(5)" class="btn">5</div>
      <div @click="number(6)" class="btn">6</div>
      <div @click="minus" class="btn operator">-</div>
      <div @click="number(1)" class="btn">1</div>
      <div @click="number(2)" class="btn">2</div>
      <div @click="number(3)" class="btn">3</div>
      <div @click="add" class="btn operator">+</div>
      <div @click="number(0)" class="btn zero">0</div>
      <div @click='dot' class="btn">.</div>
      <div @click='equal' class="btn operator">=</div>

  </div>
</template>

<script>
export default {
    data(){
        return {
            previous:null,
            current:'',
            operator:null,
            operatorClicked:false

        }
    },
    methods:{
        clear(){
            this.current='';
        },

        sign(){
            if(!this.current==''){
            this.current=this.current.charAt(0)==='-' ? 
             this.current.slice(1) : `-${this.current}`;
        }
        },

        percent(){
            this.current=`${parseFloat(this.current)/100}`;

        },

        number(data){
            if(this.operatorClicked){
                this.current='';
                this.operatorClicked=false;
            }
            this.current=`${this.current}${data}`
        },
        dot(){
            if(this.current.indexOf('.')===-1) {
                this.number('.'); 
            }
        },

        setPrevious(){
            this.previous=this.current;
            this.operatorClicked=true;
        },

        divide(){
            this.operator=(a,b)=> a / b;
            this.setPrevious();

        },
        multiply(){
            this.operator=(a,b)=> a * b;
            this.setPrevious();
        },
        minus(){
            this.operator=(a,b)=> a - b;
            this.setPrevious();

        },
        add(){
            this.operator=(a,b)=>  a + b;
            this.setPrevious();

        },
        equal(){
         this.current=  `${this.operator(
                
            parseFloat(this.previous),
            parseFloat(this.current)
            
            )}`;
            this.previous=null;
            

        }

    },
    computed:{
        
    }
  
}
</script>

<style scoped>
.calculator{
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-auto-rows: minmax(50px,auto);
    font-size: 40px;
    text-align: center;
    width: 400px;
    margin: 100px auto;
}
.display{
    grid-column: 1/5;
    text-align: center;
    background:#333;
    color: white;
}
.zero{
    grid-column: 1/3
}
.btn{
    background: #f2f2f2;
    border:1px solid #999; 
    cursor: pointer;
}
.operator{
    background: orange;
}

</style>
