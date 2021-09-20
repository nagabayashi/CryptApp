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
       <div class="coin-name">
        <h4>{{ value }}</h4>
       </div>
      <div class="coin-rate">
        <h4>レート</h4>
      </div>
      <div class="coin-time">
        <h4>更新時間</h4>
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

axios.defaults.baseURL = 'http://localhost:8080';
axios.defaults.headers.get['Content-Type'] = 'application/json;charset=utf-8';
// axios.defaults.headers.get['Access-Control-Allow-Origin'] = 'https://api.coin.z.com"';
axios.defaults.headers.get['Access-Control-Allow-Credential'] = true;

export default {
  props:["Value"],
  data(){
    return{
      value:"",
    };
  },
  async mounted() {
    // axios.defaults.headers.post['Access-Control-Allow-Origin'] = '*';
    // const url = await axios.get(`https://api.coin.z.com/public/v1/ticker?symbol=BTC`)
    // const coinData = url.symbol;
    // console.log (url.symbol)
    // this.value = coinData.value;
    axios.get(`https://api.coin.z.com/public/v1/ticker?symbol=BTC`)
    .then(function(response){
      console.log(response.data.value)
      this.value = response.data.value
    }.bind(this))
    .catch (function (error) {
      console.log(error)
    })
  },
};
</script>

<style>
body {
  background: #eee;
}
.about {
  width: 100%;
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
}
.list-name-1{
  width: 30%;
  text-align: center;
  margin: 0 20px;

}
.list-name-2{
  width: 35%;
  text-align: center;
  margin: 0 20px;
}
.list-name-3{
  width: 35%;
  text-align: center;
  margin: 0 20px;
}

.coin-detail{
  display: flex;
  justify-content: space-around;
  align-items: center;
}

.coin-detail h4{
  margin: 8px 0;
  /* font-size: 12px; */
}
.coin-name{
  width: 30%;
  border: #5ACB94 solid 1px;
  margin: 0 20px;
  border-radius: 5px;
  justify-content: center;
}
.coin-rate{
  width: 35%;
  border: #5ACB94 solid 1px;
  margin: 0 20px;
  border-radius: 5px;
  justify-content: center;
}
.coin-time{
  width: 35%;
  border: #5ACB94 solid 1px;
  margin: 0 20px;
  border-radius: 5px;
  justify-content: center;
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