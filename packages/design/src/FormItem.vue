<template>
  <component class="tmagic-design-form-item" :is="uiComponent" v-bind="uiProps">
    <template #label>
      <slot name="label"></slot>
    </template>
    <slot></slot>
  </component>
</template>

<script setup lang="ts">
import { computed } from 'vue';

import { getDesignConfig } from './config';
import type { FormItemProps } from './types';

defineOptions({
  name: 'TMFormItem',
});

const props = defineProps<FormItemProps>();

const ui = getDesignConfig('components')?.formItem;

const uiComponent = ui?.component || 'el-form-item';

const uiProps = computed<FormItemProps>(() => ui?.props(props) || props);
</script>
