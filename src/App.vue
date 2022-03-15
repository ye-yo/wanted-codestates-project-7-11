<template>
  <Result
    :user="userData"
    :company="companyData"
    :left="leftResult"
    :right="rightResult"
  />
</template>

<script>
import enterprise from "./datas/enterprise.json";
import user from "./datas/user.json";
import Result from "./components/Result.vue";
import { ref } from "vue";

export default {
  data() {
    const userData = ref(Object.values(user));
    const companyData = ref(Object.values(enterprise[0].result));
    const leftResult = ["적극성", "자신감", "책임감", "개인성향", "수평사고"];
    const rightResult = ["수동성", "신중함", "무심함", "조직성향", "위계사고"];

    return {
      userData,
      companyData,
      leftResult,
      rightResult,
    };
  },
  components: { Result },
};
</script>
