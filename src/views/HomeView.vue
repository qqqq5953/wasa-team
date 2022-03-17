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

export default {
  name: 'HomeView',
  components: {
    inputComponent,
    outputComponent
  },
  data() {
    return {
      type: 'text',
      output: ''
    }
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
