<template>
  <div class="home flex">
    <CryptList v-for="(data, index) in lists" :key="index" :Value="data.Value" :Description="data.Description" />
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
          Description: "ビットコイン(現物取引)",
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
.flex {
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
}
</style>