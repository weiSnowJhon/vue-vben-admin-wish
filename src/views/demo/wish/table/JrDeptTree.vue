<!-- 预置列表 -->
<template>
  <div class="w-100">
    <div class="w-full m-4 mr-0 overflow-hidden bg-white">
      <a-space>
        <home-outlined />
        <setting-filled />
        <smile-outlined />
        <sync-outlined spin />
        <smile-outlined :rotate="180" />
        <loading-outlined />
      </a-space>
    </div>
    <div class="w-full m-4 mr-0 overflow-hidden bg-white">
      <BasicTree
        toolbar
        treeWrapperClassName="h-[calc(100%-35px)] overflow-auto"
        :clickRowToExpand="false"
        :treeData="treeData"
        :fieldNames="{ key: 'id', title: 'deptName' }"
        @select="handleSelect"
      />
    </div>
  </div>
</template>
<script lang="ts" setup>
  import { onMounted, ref } from 'vue';
  import {
    HomeOutlined,
    SettingFilled,
    SmileOutlined,
    SyncOutlined,
    LoadingOutlined,
  } from '@ant-design/icons-vue';
  import { BasicTree, TreeItem } from '@/components/Tree';
  // import { getDeptList } from '@/api/demo/system';

  defineOptions({ name: 'JrDeptTree' });

  const emit = defineEmits(['select']);

  const treeData = ref<TreeItem[]>([
    {
      id: 1,
      deptName: '预置方案',
      children: [
        {
          id: 2,
          deptName: '预置方案1',
        },
        {
          id: 3,
          deptName: '预置方案2',
        },
      ],
    },
    {
      id: 4,
      deptName: '公共方案',
      children: [
        {
          id: 5,
          deptName: '公共方案1',
        },
        {
          id: 6,
          deptName: '公共方案2',
        },
      ],
    },
    {
      id: 7,
      deptName: '个人方案',
      children: [
        {
          id: 8,
          deptName: '个人方案1',
        },
        {
          id: 9,
          deptName: '个人方案2',
        },
      ],
    },
  ]);

  async function fetch() {
    // treeData.value = (await getDeptList()) as unknown as TreeItem[];
  }

  function handleSelect(keys) {
    emit('select', keys[0]);
  }

  onMounted(() => {
    fetch();
  });
</script>
