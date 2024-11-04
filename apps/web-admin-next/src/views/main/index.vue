<script setup>
import { ref } from 'vue';
import { useRoute } from 'vue-router';

import { Button as AButton, Input as AInput } from 'ant-design-vue';

import { mainApi } from '#/api';

const value = ref('');

// 获取当前路由对象
const route = useRoute();

function initPage() {
  const params = route.meta.menuParams;
  params.pageNum = 1;
  params.numPerPage = 20;
  delete params.otherProperties;
  mainApi(params)
    .then((res) => {
      // 处理成功响应
      console.log('API 请求成功:', res);
      // 可以在这里处理返回的数据，例如显示在页面上
      // this.dataSource = res.data.data;
    })
    .catch((error) => {
      console.error('API 请求失败:', error);
      // 可以在这里添加更多的错误处理逻辑，例如显示错误提示
    });
}

initPage();
</script>

<template>
  <div>
    <div>MAIN</div>
    <AButton type="primary">Primary Button</AButton>
    <AInput v-model:value="value" placeholder="Basic usage" />
  </div>
</template>

<style scoped></style>
