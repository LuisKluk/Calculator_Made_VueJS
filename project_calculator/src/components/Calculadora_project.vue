<template>
  <link
  href="https://fonts.googleapis.com/css2?family=Red+Hat+Display:wght@500&display=swap"
  rel="stylesheet"
/>
<link
  href="https://fonts.googleapis.com/css2?family=Fira+Sans:wght@500&display=swap"
  rel="stylesheet"
/>

    <div class="calculator">
      <div class="screen">
        <div class="screenContent">
          <p class="calculation">
            <span id="calculationText"></span>
          </p>
          <p class="result">
            <span id="resultText">{{ result }}</span>
          </p>
        </div>
      </div>
      <table>
      <tr>
        <td><input v-on:click="resetAll()" class="btn operator" type="button" value="C" /></td>
        <td><input v-on:click="limparCampo()" class="btn operator" type="button" value="<" /></td>
        <td><input v-on:click="operationDiv()" class="btn math" type="button" value="/" /></td>
        <td><input v-on:click="operationMult()" class="btn math" type="button" value="x" /></td>
      </tr>
      <tr>
        <td><input v-on:click="onClick(7)" class="btn" type="button" value="7" /></td>
        <td><input v-on:click="onClick(8)" class="btn" type="button" value="8" /></td>
        <td><input v-on:click="onClick(9)" class="btn" type="button" value="9" /></td>
        <td><input v-on:click="operation_Sub()" class="btn math" type="button" value="-" /></td>
      </tr>
      <tr>
        <td><input v-on:click="onClick(4)" class="btn" type="button" value="4" /></td>
        <td><input v-on:click="onClick(5)" class="btn" type="button" value="5" /></td>
        <td><input v-on:click="onClick(6)" class="btn" type="button" value="6" /></td>
        <td><input v-on:click="operation_Adi()" class="btn math" type="button" value=" +" /></td>
      </tr>
      <tr>
        <td><input v-on:click="onClick(1)" class="btn" type="button" value="1" /></td>
        <td><input v-on:click="onClick(2);" class="btn" type="button" value="2" /></td>
        <td><input v-on:click="onClick(3);" class="btn" type="button" value="3" /></td>
        <td rowspan="2">
          <input
            v-on:click="showResult()"
            style="height: 100px"
            class="btn operator"
            type="button"
            value="="
          />
        </td>
      </tr>
      <tr>
        <td colspan="2">
          <input v-on:click="onClick(0)" style="width:100px" class="btn" type="button" value="0" />
        </td>
        <td><input v-on:click="onClick('.')" class="btn" type="button" value="." /></td>
      </tr>
    </table>
    </div>
    
    </template>
    
    <script>
    
    export default {
    data(){
        return{
            result: 0,
            numero01: 0,
            numero02: 0,
            operation: ''

        }
    },
      components: {
        
      },
      computed:{
        },
      methods:{
        onClick(numero){
          this.result = `${this.result + numero}`
          

        },
        limparCampo(){
          if(this.result.length == 1){
            this.result = 0 ;
          }else if(this.result == 0){
            this.result = 0 ;
          }
          else{
            this.result=this.result.slice(0,-1);
          } 
        },
        resetAll(){
          this.result = 0
          this.numero01 = 0
          this.numero02 = 0
        },
        operation_Adi(){
          if(this.result != 0){
            this.numero01 = parseInt(this.result);
            this.operation = 'adi'
          }
          
          console.log(this.numero01)
          this.result = 0;
            
        },
        operation_Sub(){
          if(this.result != 0){
            this.numero01 = parseInt(this.result);
            this.operation = 'sub'
          }
            this.result = 0;
          },
        operationMult(){
          if(this.result != 0){
            this.numero01 = parseInt(this.result);
            this.operation = 'mult'
          }
            this.result = 0;
          },
        operationDiv(){
          if(this.result != 0){
            this.numero01 = parseInt(this.result);
            this.operation = 'div'
          } 
            this.result = 0;
          },
        showResult(){
          switch(this.operation){
            case "adi":
            this.numero02 = parseInt(this.result);
            this.result = this.numero01 + this.numero02
            this.result = `${this.result}`
            console.log(this.numero02)
            break

            case "sub":
            this.numero02 = parseInt(this.result);
            this.result = this.numero01 - this.numero02
            this.result = `${this.result}`
            console.log(this.numero02)
            break

            case "mult":
            this.numero02 = parseInt(this.result);
            this.result = this.numero01 * this.numero02
            this.result = `${this.result}`
            console.log(this.numero02)
            break

            case "div":
            this.numero02 = parseInt(this.result);
            this.result = this.numero01 / this.numero02
            this.result = `${this.result}`
            console.log(this.numero02)
            break
          }
        }

      }
    }
    </script>
    
    <style>
    
     .calculator {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translateX(-50%) translateY(-50%);
      border-radius: 15px;
      overflow: hidden;
    }
    .screen {
      height: 150px;
      background: #001e34;
      margin: 20px 20px 20px 20px;
      margin: auto;
    }
    
    .screenContent {
      text-align: end;
      padding: 17px;
      font-size: 30px;
      user-select: none;
    }
    
    .calculation {
      font-size: 1px;
      color: white;
      overflow: auto;
      padding-top: 2rem;
    }
    
    .result {
      font-size: 2.5rem;
      padding-top: 1rem;
      color: #fff;
    }
    
    table {
      background-color: #001e34;
      border-collapse: collapse;
    }
    
    tr,
    td {
      border: 0.2px solid black;
      border-collapse: collapse;
    }
    
    .btn {
      width: 50px;
      height: 50px;
      font-size: 17px;
      cursor: pointer;
      border: none;
      background: #002b4a;
      color: white;
      outline: none;
    }
    
    .operator {
      color: #26b821;
      font-family: "Fira Sans", sans-serif;
    }
    
    .math {
      color: #9a80e4;
      font-family: "Fira Sans", sans-serif;
    }
    
    input[type="button"]:hover {
      background-color: #ffa800;
      color: #fff;
      transition: all 0.5s linear;
    }
     
    </style>
    