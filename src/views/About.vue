<template>
  <div class="about">
    <div class="home-title">
      <img src="../../public/仮想通貨イメージpng.png" alt="blank">
      <h4>通貨詳細</h4>
    </div>
    <div class="list-namebox">
      <div class="list-name-1">
        <h4>通貨</h4>
      </div>
      <div class="list-name-2">
       <h4>最終取引価格</h4>
      </div>
      <div class="list-name-3">
        <h4>更新時間</h4>
      </div>
    </div>
    <div class="coin-detail">
       <div class="list-title">
        <h4>通貨{{ Value }}</h4>
       </div>
      <div class="list-detail">
        <h4>レート{{ Description }}</h4>
      </div>
    </div>
    <div class="home-link">
      <button>
        <a @click="$router.push({name:'Home'})" class="home-button">戻る</a>
      </button>
    </div>
  </div>
</template>

<script>
import axios from "axios"
export default {
  props:["Value,Description"],
  data(){
    return{
      Value:"",
      Description:"",
    };
  },
  async created() {
    const item = await axios.get(
      'https://api.coin.z.com/public/v1/ticker?symbol=${this.value}'
    );
    const coinData = item.data;
    this.value = coinData.value;
    this.description = coinData.description;
  },
};
</script>

<style>
body {
  background: #eee;
}
.about {
  width: 80%;
  flex-wrap: wrap;
  margin: auto;
  color: #1B5B63;
  background: #eee;
}
.home-title{
  display: flex;
  align-items: center;
}
.home-title img{
  width: 40px;
  height: auto;
}
.home-title h4{
  text-align: left;
  padding-left: 10px;
}
.list-namebox{
  display: flex;
  justify-content: space-around;
  padding: 0 10px;
}
.list-name-1{
  width: 30%;
  text-align: left;
  margin: 0 20px;

}
.list-name-2{
  width: 35%;
  text-align: left;
  margin: 0 10px;
}
.list-name-3{
  width: 35%;
}
.home-link{
  margin: 100px;
}
 .home-link button{
   box-shadow:1px 2px rgb(138, 138, 138);
   border: rgb(224, 224, 224) solid 0.5px ;
   border-radius: 10px;
   padding: 5px 10px;

  }
.home-link a {
  text-decoration: none;
  color: #1B5B63;
  font-weight: bold;
  margin: 0 10px;
  cursor: pointer;
}
.home-link a:hover {
  color: #22abc0;
  
}
</style>