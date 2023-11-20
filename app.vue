<script lang='ts'>
import { defineComponent, ref } from 'vue'
import {
  darkTheme,
  NConfigProvider, NDialogProvider,
  NLoadingBarProvider,
  NMessageProvider,
  NNotificationProvider,
} from 'naive-ui'
import type { GlobalTheme } from 'naive-ui'
import DefaultLayout from '~/layouts/default.vue'

export default defineComponent({
  components: { NDialogProvider, NLoadingBarProvider, NNotificationProvider, NMessageProvider, DefaultLayout, NConfigProvider },
  setup() {
    return {
      darkTheme
    }
  }
})
</script>

<template>
  <NConfigProvider :theme="darkTheme">
    <NMessageProvider>
      <NNotificationProvider>
        <NLoadingBarProvider>
          <NDialogProvider>
            <DefaultLayout />
          </NDialogProvider>
        </NLoadingBarProvider>
      </NNotificationProvider>
    </NMessageProvider>
  </NConfigProvider>
</template>
