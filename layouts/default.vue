<template>
  <div>
    <n-space vertical size="large">
      <NSpace vertical>
        <Provided />
      </NSpace>
      <n-layout has-sider sider-placement="right">
        <n-layout style="max-height: 320px">
          <NuxtPage page-key="static" />
        </n-layout>
        <n-layout-sider
          bordered
          show-trigger
          collapse-mode="width"
          :collapsed-width="64"
          :width="240"
          :native-scrollbar="false"
          style="max-height: 320px"
        >
          <n-menu
            :collapsed-width="64"
            :collapsed-icon-size="22"
            :options="menuOptions"
          />
        </n-layout-sider>
      </n-layout>
    </n-space>
  </div>
</template>

<script lang='ts'>
import { h, defineComponent, Component, ref } from 'vue'
import { NLayout, NLayoutSider, NMenu, NSpace, NIcon, NButton, NCard, darkTheme, GlobalTheme } from 'naive-ui'
import {
  BookOutline as BookIcon,
  PersonOutline as PersonIcon,
  WineOutline as WineIcon
} from '@vicons/ionicons5'
import Provided from '~/Provided.vue'

export default {
  name: 'DefaultLayout',
  components: { NCard, NButton, Provided, NMenu, NLayoutSider, NLayout, NSpace, NIcon },
  data() {
    return {
      darkTheme,
      theme: null,
      menuOptions: [
        {
          label: 'Hear the Wind Sing',
          key: 'hear-the-wind-sing',
          icon: this.renderIcon(BookIcon)
        },
        {
          label: 'Pinball 1973',
          key: 'pinball-1973',
          icon: this.renderIcon(BookIcon),
          disabled: true,
          children: [
            {
              label: 'Rat',
              key: 'rat'
            }
          ]
        },
        {
          label: 'A Wild Sheep Chase',
          key: 'a-wild-sheep-chase',
          disabled: true,
          icon: this.renderIcon(BookIcon)
        },
        {
          label: 'Dance Dance Dance',
          key: 'Dance Dance Dance',
          icon: this.renderIcon(BookIcon),
          children: [
            {
              type: 'group',
              label: 'People',
              key: 'people',
              children: [
                {
                  label: 'Narrator',
                  key: 'narrator',
                  icon: this.renderIcon(PersonIcon)
                },
                {
                  label: 'Sheep Man',
                  key: 'sheep-man',
                  icon: this.renderIcon(PersonIcon)
                }
              ]
            },
            {
              label: 'Beverage',
              key: 'beverage',
              icon: this.renderIcon(WineIcon),
              children: [
                {
                  label: 'Whisky',
                  key: 'whisky'
                }
              ]
            },
            {
              label: 'Food',
              key: 'food',
              children: [
                {
                  label: 'Sandwich',
                  key: 'sandwich'
                }
              ]
            },
            {
              label: 'The past increases. The future recedes.',
              key: 'the-past-increases-the-future-recedes'
            }
          ]
        }
      ]
    }
  },
  methods: {
    renderIcon (icon: Component) {
      return () => h(NIcon, null, { default: () => h(icon) })
    }
  }
}
</script>

<style>

</style>

