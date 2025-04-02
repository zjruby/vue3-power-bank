<template>
  <a-layout style="min-height: 100vh">
    <a-layout-sider v-model:collapsed="collapsed" collapsible>
      <div class="logo" />
      <a-menu v-model:selectedKeys="selectedKeys" theme="dark" mode="inline">
        <a-menu-item key="1">
          <pie-chart-outlined />
          <span>首页</span>
        </a-menu-item>
        <a-menu-item key="2">
          <desktop-outlined />
          <span>文档</span>
        </a-menu-item>
        <a-sub-menu key="sub1">
          <template #title>
            <span>
              <user-outlined />
              <span>User</span>
            </span>
          </template>
          <a-menu-item key="3">Tom</a-menu-item>
          <a-menu-item key="4">Bill</a-menu-item>
          <a-menu-item key="5">Alex</a-menu-item>
        </a-sub-menu>
        <a-sub-menu key="sub2">
          <template #title>
            <span>
              <team-outlined />
              <span>Team</span>
            </span>
          </template>
          <a-menu-item key="6">Team 1</a-menu-item>
          <a-menu-item key="8">Team 2</a-menu-item>
        </a-sub-menu>
        <a-menu-item key="9">
          <file-outlined />
          <span>File</span>
        </a-menu-item>
      </a-menu>
    </a-layout-sider>
    <!-- 侧边栏 -->

    <a-layout>
      <a-table :columns="columns" :data-source="data" :scroll="{ x: 1500, y:610}"  :bordered="false"  size="large">
        <template #bodyCell="{ column }">
          <template v-if="column.key === 'operation'">
            <a>123</a>
          </template>
        </template>
      </a-table>
    </a-layout>

  </a-layout>
</template>

<script lang="ts">
export default {
  name: "index",
};                       
</script>

<script setup lang="ts">
import {
  PieChartOutlined,
  DesktopOutlined,
  UserOutlined,
  TeamOutlined,
  FileOutlined,
} from "@ant-design/icons-vue";//图片
import type { TableColumnsType } from 'ant-design-vue';
import { Content } from "ant-design-vue/es/layout/layout";
import { ref } from "vue";

const collapsed = ref<boolean>(false);//false收紧
const selectedKeys = ref<string[]>(["1"]);//双向绑定数据

const columns: TableColumnsType = [
  { title: 'Full Name', width: 120, dataIndex: 'name', key: 'name', fixed: 'left' },
  { title: 'Age', width: 80, dataIndex: 'age', key: 'age', fixed: 'left' },
  { title: 'Column 1', dataIndex: 'address', key: '1', width: 200 },
  { title: 'Column 2', dataIndex: 'address', key: '2', width: 200 },
  { title: 'Column 3', dataIndex: 'address', key: '3', width: 200 },
  { title: 'Column 4', dataIndex: 'address', key: '4', width: 200 },
  { title: 'Column 5', dataIndex: 'address', key: '5', width: 200 },
  { title: 'Column 6', dataIndex: 'address', key: '6', width: 200 },
  { title: 'Column 7', dataIndex: 'address', key: '7', width: 200 },
  { title: 'Column 8', dataIndex: 'address', key: '8', width: 200 },
  {
    title: 'Action',
    key: 'operation',
    fixed: 'right',
    width: 100,
  },
];

interface DataItem {
  key: number;
  name: string;
  age: number;
  address: string;
}

const data: DataItem[] = [];
for (let i = 0; i < 100; i++) {
  data.push({
    key: i,
    name: `Edrward ${i}`,
    age: 32,
    address: `London Park no. ${i}`,
  });
}
</script>

<style scoped>
.logo {
  height: 32px;
  margin: 16px;
  background-image: url(../../img/交个朋友.jpeg);
  background-repeat: no-repeat;
  background-size: cover;
}
</style>
