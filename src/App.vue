<template>
  <chart-pentagon
    :user-result="userResult"
    :enterprise-result="enterpriseResult"
  />
  <h1 class="tag active">자동 배포 성공?</h1>
</template>

<script>
import ChartPentagon from "./components/ChartPentagon.vue";
import user from "./datas/user.json";
import enterprise from "./datas/enterprise.json";
export default {
  components: { ChartPentagon },
  data() {
    return {
      message: "Hello Vue!!!",
      userResult: Object.values(user),
      enterpriseResult: Object.values(enterprise),
    };
  },
};
</script>
<style lang="scss" scoped>
.tag {
  &.active {
    background-color: black;
  }
}
</style>
