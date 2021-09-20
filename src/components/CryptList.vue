<template>
  <div class="list">
    <div class="list-title">
      <h1>{{ Symbol }}</h1>
    </div>
    <div class="list-detail">
      <h1>{{ Description }}</h1>
    </div>
    <div class="list-link">
      <button>
      <a @click="$router.push({ name: 'About', params: { Value: Symbol }})">詳細</a>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  props: ["Symbol","Description"],
};
</script>

<style scoped>
.list {
  background: #fff;
  position: relative;
  display: flex;
  align-items: center;
  justify-content: space-around;
}

.list-title {
  width: 20%;
  font-size: 8px;
  text-align: left;
  color: #1B5B63;
  margin: 5px 20px;
  text-align: left;
}
.list-detail{
  width: 60%;
  font-size: 8px;
  margin: 5px 10px;
  color: #1B5B63;
  text-align: left;

}
.list-link {
  width: 20%;
  text-align: center;
  margin:  5px 10px;
}
 .list-link button{
   box-shadow:1px 2px rgb(138, 138, 138);
   border: rgb(224, 224, 224) solid 0.5px ;
   border-radius: 10px;
   padding: 5px 10px;

  }
.list-link a {
  text-decoration: none;
  color: #1B5B63;
  font-weight: bold;
  margin: 0 10px;
  cursor: pointer;
}
.list-link a:hover {
  color: #003841;
}
</style>