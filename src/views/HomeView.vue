<template>
  <div class="container">
    <CusInput class="my-input" custom="outline" placeholder="测试输入" v-model="inputText"></CusInput>
    <CusMenuVue :itemList=itemList></CusMenuVue>
  </div>
</template>

<script>
import CusInput from "@/components/CusInput.vue"
import CusMenuVue from "@/components/CusMenu.vue";
export default {
  name: 'HomeView',
  components: {
    CusInput,
    CusMenuVue
  },
  data: function () {
    return {
      inputText:"",
      fatherData:"父组件数据",
      itemList: [{
        name: "测试1",
        icon: "el-icon-s-tools",
        click: function () {
         console.log("这是点击事件1")
        }
      }, {
        name: '测试2',
        icon: "el-icon-warning",
        click: function () {
          console.log("这是点击事件2")
        }
      },
      {
        name: '测试2',
        icon: "el-icon-upload",
        click: function () {
          console.log("这是点击事件3")
        }
      }]
    }
  }
}
</script>
<style scoped lang="scss">
.container {
  width: 100%;
  position: relative;

  .my-input {
    position: absolute;
    top: 250px;
    left: 50px;
  }
}
</style>