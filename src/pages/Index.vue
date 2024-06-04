<template>
  <el-container style="height: 100vh">
    <el-aside width="200px">
      <el-menu :default-openeds="['1']">
        <el-submenu index="1">
          <template #title>销售管理</template>
          <el-menu-item index="1-1">客户管理</el-menu-item>
          <el-menu-item index="1-2">线索管理</el-menu-item>
          <el-menu-item index="1-3">合同管理</el-menu-item>
        </el-submenu>
      </el-menu>
    </el-aside>
    <el-container>
      <el-header>
        <el-input v-model="filter" placeholder="筛选..."></el-input>
      </el-header>
      <el-main>
        <el-table :data="filteredData">
          <el-table-column prop="a" label="A"></el-table-column>
          <el-table-column prop="b" label="B"></el-table-column>
          <el-table-column prop="c" label="C"></el-table-column>
        </el-table>
      </el-main>
    </el-container>
  </el-container>
</template>

<script>
import { ref, computed } from "vue";

export default {
  setup() {
    const filter = ref("");
    const data = ref([
      { a: "Data 1", b: "Data 2", c: "Data 3" },
      { a: "Data 4", b: "Data 5", c: "Data 6" },
      { a: "Data 7", b: "Data 8", c: "Data 9" },
    ]);

    const filteredData = computed(() => {
      if (!filter.value) return data.value;
      return data.value.filter((item) => Object.values(item).some((val) => val.includes(filter.value)));
    });

    return {
      filter,
      filteredData,
    };
  },
};
</script>

<style>
body {
  margin: 0;
}
</style>
