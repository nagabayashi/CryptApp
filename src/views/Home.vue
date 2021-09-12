<template>
  <div class="home">
    <div class="home-title">
      <img src="../../public/仮想通貨イメージpng.png" alt="blank">
      <h4>通貨一覧</h4>
    </div>
    <div class="list-namebox">
      <div class="list-name-1">
        <h4>通貨</h4>
      </div>
      <div class="list-name-2">
       <h4>説明</h4>
      </div>
      <div class="list-name-3">
        <h4></h4>
      </div>
    </div>
    <div class="coin-list">
      <CryptList v-for="(data, index) in lists" :key="index" :Value="data.Value" :Description="data.Description" />
    </div>
  </div>
</template>

<script>
import CryptList from "../components/CryptList";
export default {
  data() {
    return {
      lists: [
        {
          Value: "BTC",
          Description: "ビットコイン（現物取引）",
        },
      ]
    };
  },
  components: {
    CryptList
  }
};
</script>

<style scoped>
body {
  background: #eee;
}
.home {
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
  width: 20%;
  text-align: left;
  margin: 0 20px;

}
.list-name-2{
  width: 60%;
  text-align: left;
  margin: 0 10px;
}
.list-name-3{
  width: 20%;
}
.coin-list{
  border: #1B5B63 2px solid;
  border-radius: 5px 5px;
  padding: 10px 10px;
}
</style>