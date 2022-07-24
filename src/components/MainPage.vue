<template>
  <div class="hello">
    <img alt="Vue logo" src="../assets/logo.png">
    <h1>Find the Levenshtein difference</h1>
    <h4>Input a string, and you will get the closest word from the list:</h4>
    <div class="box">
      <div>
        <label for="input1">Input word</label>
        <input id="input1" type="text" v-model="input1">
      </div>
    </div>
    <button @click="findDifference">Find similar words</button>
    <h4>Most similar words(with difference = {{curDiff}}):</h4>
    <div v-for="el in resultArr">{{el}}</div>
  </div>
  <div class="rightBox">
    <ul>
      <li v-for="el in dataArr">{{el}}</li>
    </ul>
  </div>
</template>

<script lang="ts">
import { Vue } from 'vue-class-component';
import search from '../scripts/levenshteinSearch';
import dataArr from '../data/dataArr';

export default class HelloWorld extends Vue {

  dataArr: string[] = dataArr
  input1: string = ''
  resultArr: (string | number)[] = []
  curDiff: number = 0

  findDifference() {
    var tmpArr = []
    var inputStr = this.input1
    var minDiff = Number.MAX_VALUE
    for(let i = 0; i < this.dataArr.length; i++){
      let searchResult = search(inputStr, this.dataArr[i])
      tmpArr.push([this.dataArr[i], searchResult])
      if(searchResult < minDiff) minDiff = searchResult
    }
    tmpArr = tmpArr.filter(item => item[1] == minDiff)
    this.curDiff = minDiff
    this.resultArr = tmpArr.map(item => item[0])
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
label{
  margin-right: 10px;
}
button{
  margin-top: 30px;
}
.hello{
  width: 70%;
  float: left;
}
.box{
  display: flex;
  gap: 50px;
  justify-content: center;
}
.rightBox{
  width: 30%;
  float: right;
  border-left: 1px solid black;
  box-sizing: border-box;
  min-height: 100vh;
}

.disableMod{
  text-decoration: none;
}
</style>
