<template>
  <div style="width: 100%">
    <client-only fallback-tag="span" fallback="Loading Table...">
      <n-data-table
        ref="nTable"
        :max-height="500"
        virtual-scroll
        style="
          --n-merged-border-color: #eff0f3;
          --n-merged-th-color: #f6f9ff;
          --n-th-text-color: #333333;
          --n-th-font-weight: bold;
          --n-th-padding: 20px;
          --n-td-padding: 10px 20px;
          --n-td-text-color: #868686;
        "
        :scrollbar-props="{
          trigger: 'none'
        }"
        :columns="tableColumns"
        :data="tableData"
        :single-line="false"
        :scroll-x="2000"
      />
    </client-only>
  </div>
</template>

<script lang="ts" setup>
import { NDataTable, DataTableColumn } from 'naive-ui'

const tableData = ref<any>(
  Array(100)
    .fill(0)
    .map((item, index) => {
      return {
        0: '222222222222222222222222222222222222222',
        1: '3'.repeat(100 * Math.random())
      }
    })
)
const tableColumns: DataTableColumn[] = Array(10)
  .fill(0)
  .map((item, index) => {
    return {
      title: `${index}`,
      key: index,
      fixed: index === 0 ? 'left' : false,
      width: 200,
      resizable: index === 1 ? true : false
    }
  })
</script>
