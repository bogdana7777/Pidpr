<template>
  <div id="app">
      <!--<h2> {{text}} </h2>
      <input v-model="text">
      <p v-if="text.length>0"> Довжина тексту {{text.length}}</p>
      <p v-else> Нема тексту </p>
      <table>
        <tr v-for="(number, index) in numbers" v-bind:key="number">
          <td> Елемент  {{index}} </td>
          <td> {{number}} </td>
          <td> <button v-on:click="alertElement(number)">  alert  </button></td>
          <td> <button v-on:click="deleteElement(index)">  Delete  </button></td>           
        </tr>
      </table>
      <input type="number" v-model="newNumber"><button v-on:click="addElement(newNumber)"> Додати число в масив</button>-->
      <table>
        <tr>
          <th> #</th>
          <th>Ім'я водія</th>
          <th>Марка машини</th>
          <th>Колір машини</th>
          <th>Номер машини</th>
        </tr>
        <tr v-for="(driver, index) in drivers" v-bind:key="driver.mark">
            <td> {{index+1}}</td>
            <td> {{driver.name}}</td>
            <td> {{driver.mark}}</td>
            <td> {{driver.color}}</td>
            <td> {{driver.number}}</td>
            <td> <button v-on:click="deleteElement(index)">  Delete  </button></td>   
            <td> <button v-on:click="editElement(index)">  Edit  </button></td>   
        </tr>
      </table>
<form v-if="bool == true">
      <label> Ім'я водія <input v-model="newDriver.name"></label>
      <label> Марка машини <input v-model="newDriver.mark"></label>
      <label> Колір машини <input v-model="newDriver.color"></label>
      <label> Номер машини <input v-model="newDriver.number"></label>
      
</form>
      <br/>
      <button type="button" v-on:click="addElement(newDriver)"> Додати водія </button> <br/><br/>
      <button v-on:click="toggleForm(newDriver)"> Додати </button> <br/><br/>
      <button v-on:click="editElement(newDriver)"> Редагувати водія </button>
  </div>
</template>

<script>
export default {
  name: 'app',
  data() {
    return {
        /*text: "Деякий текст",
        numbers: [1,3,-5,2,6,9],
        newNumber:0*/
        newDriver:{name:"", mark:"",price:"",number:""},
        drivers: [{name:"Горей Л.", mark:"Mercedes",color:"black",number:"AO 2378 AI"},{name:"Половко І.", mark:"Volkswagen",color:"white",number:"AO 2329 AI"}],
        bool: false
    }
  } ,
  methods:{

    addElement:function(){
      this.bool = true;
    },

    deleteElement: function(index){
      this.drivers.splice(index,1);
    },
    editElement:function(index){
      let copy = Object.assign({}, index);   
      this.drivers.push(copy);
    },
    toggleForm:function(value){
      let copy = Object.assign({}, value);   
      this.drivers.push(copy);
      this.bool = false;
    },
    editElement:function(index){

    }
  } 
}
</script>

<style scoped>
  table td{
    border: 1px solid black;
    border-collapse: collapse;
    width: 100px;
  }
</style>