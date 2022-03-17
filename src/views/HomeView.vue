<template>
  <button @click="toggleTheme" class="btn">toggle theme</button>
  <div class="inputField">
    <div class="button-group">
      <button class="btn" @click="inputType = 'text'">input text</button>
      <button class="btn" @click="inputType = 'radio'">input radio</button>
      <button class="btn" @click="inputType = 'select'">select menu</button>
    </div>
    <inputComponent :inputType="inputType" @emitOutput="receiveOutput" />
    <outputComponent :output="output" />
  </div>
</template>

<script>
import inputComponent from '@/components/inputComponent.vue'
import outputComponent from '@/components/outputComponent.vue'
import { useMeta } from 'vue-meta'
import { ref } from 'vue'

export default {
  setup() {
    useMeta({
      title: 'Andy Hsieh',
      description: [
        {
          content:
            '山葵組WasaTeam創立於2016年，主攻網頁、APP、系統規劃設計與開發，過去累積了不少大大小小專案和客戶，平時也喜歡研究一些哩哩叩叩好玩的網頁特效應用在作品上，目前團隊8個人，都是90後年輕人，是能夠輕鬆溝通但絕不馬虎隨便的工作氣氛'
        }
      ]
    })

    const type = ref('text')
    const output = ref('')

    return {
      type,
      output
    }
  },
  name: 'HomeView',
  components: {
    inputComponent,
    outputComponent
  },
  computed: {
    inputType: {
      get() {
        return this.type
      },
      set(val) {
        this.type = val
      }
    }
  },
  methods: {
    toggleTheme() {
      document.body.classList.toggle('dark')
    },
    receiveOutput(val) {
      this.output = val
    }
  }
}
</script>

<style scoped lang="scss">
.inputField {
  background-color: rgb(187, 187, 187);
  box-shadow: 0 4px 10px 1px var(--box-shadow-color);
  border-radius: 0.25rem;
  padding: 2rem;
  margin-top: 1rem;
}

.button-group {
  display: flex;
  gap: 1rem;
  margin-bottom: 1rem;
}

.btn {
  padding: 0.5rem 0.75rem;
  font-size: 1.5rem;
  color: var(--button-text-color);
  background-color: var(--accent-color);
  border: none;
  border-radius: 0.25rem;
  cursor: pointer;

  &:hover,
  &:focus {
    background-color: var(--button-hover-color);
  }
}
</style>
