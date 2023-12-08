<template>
  <div class="page">
    <NSpace vertical size="small">
      <n-layout style="height: calc(100vh - 30px)">
        <n-layout-header style="height: 64px; padding: 24px 12px" bordered>
          <div
            v-html="title"
            class="the-container"
            style="
              font-family: 'Times New Roman', sans-serif;
              font-size: 1.4rem;
              line-height: 0.8rem;
            "
          />
        </n-layout-header>
        <n-layout has-sider position="absolute" style="top: 64px; bottom: 64px">
          <n-layout-content
            ref="contentRef"
            content-style="padding: 10px 10px;"
            :native-scrollbar="true"
            class="the-container"
          >
            <n-space horizontal>
              <n-button-group style="margin-bottom: 20px">
                <n-tooltip
                  v-for="cta in controls"
                  :style="{ maxWidth: '200px' }"
                  trigger="hover"
                  placement="bottom"
                >
                  <template #trigger>
                    <n-button
                      @click="reverse(cta.name)"
                      strong
                      secondary
                      :style="poem.mode === cta.name ? 'cursor: not-allowed !important' : ''"
                      :type="
                        poem.mode === cta.name
                          ? cta.name === 'Refugees'
                            ? 'primary'
                            : 'error'
                          : 'default'
                      "
                    >
                      {{ cta.name }}
                    </n-button>
                  </template>
                  {{ getTip(cta, poem.mode) }}
                </n-tooltip>
              </n-button-group>
            </n-space>
            <div
              v-for="(verse, i) in poem.verses"
              style="
                font-size: .75rem;
                font-family: Tahoma, 'Times New Roman', serif;
                line-height: 1.3rem;
              "
            >
              <span style="opacity: 0.2; font-family: Consolas, monospace">{{
                verse.id + '. '
              }}</span
              ><span>{{ verse.text }}</span>
            </div>
          </n-layout-content>
        </n-layout>
        <n-layout-footer bordered position="absolute" style="height: 64px; padding: 24px">
          <NSpace horizontal justify="space-between">
            <span>The Power of Words™</span>
            <span>by <a href="mailto:deus.h@outlook.com">Amadeus H.</a></span>
          </NSpace>
        </n-layout-footer>
      </n-layout>
    </NSpace>
  </div>
</template>

<script lang="ts">
import {
  NButton,
  NButtonGroup,
  NCard,
  NH2,
  NLayout,
  NLayoutContent,
  NLayoutFooter,
  NLayoutHeader,
  NSpace,
  NTooltip
} from 'naive-ui'

export default {
  name: 'Refugees',
  components: {
    NTooltip,
    NButton,
    NButtonGroup,
    NCard,
    NH2,
    NLayout,
    NLayoutContent,
    NLayoutFooter,
    NLayoutHeader,
    NSpace
  },
  data() {
    return {
      title: '<b>BEGGARS</b> AND <b>REFUGEES</b>',
      controls: [
        {
          id: 'beggars',
          name: 'Beggars',
          tips: {
            active:
              'This is how a lower human thinks. Click Refugees to reverse & see how a higher human thinks.',
            inactive: 'Click to read in reverse, as a lower human would think.'
          }
        },
        {
          id: 'refugees',
          name: 'Refugees',
          tips: {
            active:
              'This is how a higher human thinks. Click Beggars to reverse & see how a lower human thinks.',
            inactive: 'Click to read in reverse, as a higher human would think.'
          }
        }
      ],
      poem: {
        mode: 'Beggars', // Or 'Refugees'
        verses: [
          {
            id: '01',
            text: 'They have no need of our help'
          },
          {
            id: '02',
            text: 'So do not tell me'
          },
          {
            id: '03',
            text: 'These haggard faces could belong to you or me'
          },
          {
            id: '04',
            text: 'Should life have dealt a different hand'
          },
          {
            id: '05',
            text: 'We need to see them for who they really are'
          },
          {
            id: '06',
            text: 'Chancers and scroungers'
          },
          {
            id: '07',
            text: 'Layabouts and loungers'
          },
          {
            id: '08',
            text: 'With bombs up their sleeves'
          },
          {
            id: '09',
            text: 'Cut-throats and thieves'
          },
          {
            id: '10',
            text: 'They are not'
          },
          {
            id: '11',
            text: 'Welcome here'
          },
          {
            id: '12',
            text: 'We should make them'
          },
          {
            id: '13',
            text: 'Go back to where they came from'
          },
          {
            id: '14',
            text: 'They cannot'
          },
          {
            id: '15',
            text: 'Share our food'
          },
          {
            id: '16',
            text: 'Share our homes'
          },
          {
            id: '17',
            text: 'Share our countries'
          },
          {
            id: '18',
            text: 'Instead let us'
          },
          {
            id: '19',
            text: 'Build a wall to keep them out'
          },
          {
            id: '20',
            text: 'It is not okay to say'
          },
          {
            id: '21',
            text: 'These are people just like us'
          },
          {
            id: '22',
            text: 'A place should only belong to those who are born there'
          },
          {
            id: '23',
            text: 'Do not be so stupid to think that'
          },
          {
            id: '24',
            text: 'The world can be looked at another way'
          }
        ]
      }
    }
  },
  methods: {
    getTip(cta: { name: string; tips: { inactive: string; active: string } }, mode: string) {
      return mode !== cta.name ? cta.tips.inactive : cta.tips.active
    },
    reverse(direction: string) {
      if (direction !== this.poem.mode) {
        this.poem.mode = direction
        this.poem.verses = [...this.poem.verses].reverse()
      } else {
        console.log('Nothing to do..')
      }
    }
  }
}
</script>

<style scoped>
.the-container {
  max-width: 460px;
  margin-left: auto;
  margin-right: auto;
}
a:link,
a:hover,
a:visited,
a:active {
  color: #db2256;
  text-decoration: none;
}
</style>
