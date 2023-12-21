<template>
  <PageWrapper dense contentFullHeight fixedHeight contentClass="flex">
    <div class="w-1/4 xl:w-1/5"></div>
    <!-- <JrDeptTree class="w-1/4 xl:w-1/5" /> -->
    <div class="w-3/4 xl:w-4/5">
      <Tabs v-model:activeKey="activeKey">
        <TabPane key="1" tab="查询">
          <div v-for="(columnAttr, index) in columnInfos" :key="index">
            <div class="w-full flex">
              <div class="w-1/10 m-1">
                <FormItem label="">
                  <span>{{ columnAttr.columnName }}</span>
                </FormItem>
              </div>
              <div class="w-1/10 m-1">
                <FormItem label="">
                  <Select v-model:value="searchInfo.type" class="w-full" placeholder="">
                    <SelectOption value="1">等于</SelectOption>
                    <SelectOption value="2">不等于</SelectOption>
                    <SelectOption value="3">包含</SelectOption>
                    <SelectOption value="4">不包含</SelectOption>
                    <SelectOption value="5">开始是</SelectOption>
                    <SelectOption value="6">结尾是</SelectOption>
                    <SelectOption value="7">区间</SelectOption>
                  </Select>
                </FormItem>
              </div>
              <div class="w-4/10 m-1">
                <FormItem label="">
                  <Select v-model:value="searchInfo.type" class="w-full" placeholder="">
                    <SelectOption value="1">等于</SelectOption>
                    <SelectOption value="2">不等于</SelectOption>
                    <SelectOption value="3">包含</SelectOption>
                    <SelectOption value="4">不包含</SelectOption>
                    <SelectOption value="5">开始是</SelectOption>
                    <SelectOption value="6">结尾是</SelectOption>
                    <SelectOption value="7">区间</SelectOption>
                  </Select>
                </FormItem>
              </div>
            </div>
          </div>
        </TabPane>
        <TabPane key="2" tab="查询条件" force-render>查询条件</TabPane>
        <TabPane key="3" tab="栏目">栏目</TabPane>
        <TabPane key="4" tab="条件格式">条件格式</TabPane>
      </Tabs>
    </div>
    <!-- <AccountModal @register="registerModal" @success="handleSuccess" /> -->
  </PageWrapper>
</template>
<script lang="ts" setup>
  import { Tabs, TabPane, FormItem, Select, SelectOption } from 'ant-design-vue';
  // import { JrDeptTree } from './JrDeptTree.vue';
  import { PageWrapper } from '@/components/Page';
  import { ref } from 'vue';

  defineOptions({ name: 'JrQueryConditionSetting' });
  const activeKey = ref('1');
  const searchInfo = ref<Recordable>({ type: '1', name: '123' });
  const columnInfos = ref([
    { columnName: '单据编码', columnType: 'string', defaultType: '1' },
    { columnName: '业务日期', columnType: 'string', defaultType: '1' },
    { columnName: '单据类型', columnType: 'string', defaultType: '1' },
    { columnName: '单据状态', columnType: 'string', defaultType: '1' },
    { columnName: '待审批人', columnType: 'string', defaultType: '1' },
  ]);
</script>
