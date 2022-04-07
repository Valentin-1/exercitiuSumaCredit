<script>
export default{
  data(){
    return{
      inpSuma: "",
      inpLuna: "",
      sumLun: 0,
      restSum: 0,
     resultList: [],
    }
  },
  methods: {
    calcCredit(){
      this.sumLun = Math.ceil(this.inpSuma / this.inpLuna);
      this.restSum = this.inpSuma - this.sumLun;
      
      this.objResult();
      console.log(this.resultList)
    },
    objResult(){
      this.resultList = [];
      for(let i = 0; i < this.inpLuna; i++){
        //if(i == this.resultList){
          //this.resultList.push({id: i+1, sumCurent: this.sumLun, rest: 0})
       // }else{
        this.resultList.push({id: i+1, sumCurent: this.sumLun, rest: this.restSum})
        this.restSum -= this.sumLun;
        //this.restSum = this.inpSuma - this.sumLun * (i+1);
        //}
      }
    }
  },
}

</script>

<template>
  <div>
    <input type="number" id="Suma" v-model="inpSuma"  placeholder="Suma"> <br>
    <input type="number" id="Data" v-model="inpLuna"  placeholder="Data">
    <br>  
    <button id="add" @click="calcCredit">Calculeaza</button>
    <div id="result" v-show="resultList.length != 0" >
      <table id="myTable">
        <tr>
          <th class="info">Luna</th>
          <th class="info">Suma pe luna</th>
          <th class="info"> Suma ramasa</th>
        </tr>

        <tr v-for="item in resultList" :key="item.id" class="info-2">
          <td class="info-2">{{item.id}}</td>
          <td class="info-2">{{item.sumCurent}}</td>
          <td class="info-2">{{item.rest}}</td>
        </tr>
      </table>
    </div>
  </div>
</template>


<style scoped>
@import "@/assets/base.css";

#result {
  margin-top: 50px;
}

#myTable{
  border: 1px solid black;
}

.info{
  border: 1px solid black;
  font-weight: bold;
  text-align: center;
  width: 120px;
}

.info-2{
  border: 1px solid black;
  text-align: center;
  width: 120px;
}

</style>