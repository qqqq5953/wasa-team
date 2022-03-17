<template>
  <div class="wrap">
    <section class="inputArea">
      <template v-if="inputType === 'text'">
        <input
          class="text"
          id="text"
          type="text"
          placeholder="Say my name..."
          v-model="output"
        />
      </template>

      <template v-else-if="inputType === 'radio'">
        <div class="radio-wrap">
          <input type="radio" id="one" value="option1" v-model="output" />
          <label for="one">option one</label>
        </div>
        <div class="radio-wrap">
          <input type="radio" id="two" value="option2" v-model="output" />
          <label for="two">option two</label>
        </div>
      </template>

      <template v-else>
        <div class="selectt-wrap">
          <select class="select" v-model="output">
            <option disabled value="">choose a team</option>
            <option v-for="team in teams" :key="team.id" :value="team.name">
              {{ team.name }}
            </option>
          </select>
          <div class="arrow-down"></div>
        </div>
      </template>
    </section>
  </div>
</template>

<script>
export default {
  props: {
    inputType: { type: String }
  },
  data() {
    return {
      output: '',
      teams: {
        team1: { name: 'wasa 1', id: '001' },
        team2: { name: 'wasa 2', id: '002' },
        team3: { name: 'wasa 3', id: '003' }
      }
    }
  },
  watch: {
    inputType() {
      this.output = ''
    },
    output() {
      this.$emit('emitOutput', this.output)
    }
  }
}
</script>

<style scoped lang="scss">
.wrap {
  background-color: var(--input-component-background-color);
  border-radius: 0.25rem;
  padding: 1.5rem;
}

.inputArea {
  color: var(--text-color);
  font-size: 1.5rem;

  .text {
    outline: none;
    border: 1px solid var(--border-color);
    border-radius: 0.25rem;
    background-color: transparent;
    padding: 0.5rem 0.75rem;
    font-size: 1.5rem;
    color: var(--text-color);

    &::placeholder {
      color: var(--box-shadow-color);
    }
  }

  .radio-wrap {
    border: 1px solid var(--border-color);
    border-radius: 0.25rem;
    padding: 0.5rem 0.75rem;

    &:first-of-type {
      margin-bottom: 1rem;
    }

    label {
      font-size: 1.5rem;
      margin-left: 0.5rem;
    }
  }

  .selectt-wrap {
    position: relative;
    display: inline-block;

    .select {
      -moz-appearance: none; /* Firefox */
      -webkit-appearance: none; /* Safari and Chrome */
      appearance: none;

      outline: none;
      border: 1px solid var(--border-color);
      border-radius: 0.25rem;
      background-color: transparent;
      padding: 0.5rem 2.25rem 0.5rem 0.75rem;
      font-size: 1.5rem;
      color: var(--text-color);
    }

    .arrow-down {
      position: absolute;
      top: 0;
      bottom: 0;
      right: 10px;
      z-index: 2;
      margin: auto;
      border-left: 10px solid transparent;
      border-right: 10px solid transparent;
      border-top: 10px solid var(--accent-color);
      width: 0px;
      height: 0px;
    }
  }
}
</style>
