<template>
  <section class="outputArea">
    Output:
    <div class="output">
      {{
        output.toLowerCase() === 'heisenberg'
          ? 'You are god darn right'
          : output
      }}
    </div>
  </section>
</template>

<script>
export default {
  props: {
    output: {
      type: String
    }
  }
}
</script>

<style lang="scss" scoped>
.outputArea {
  display: flex;
  align-items: center;
  margin-top: 1rem;
  color: var(--text-color);
  font-size: 1.5rem;

  .output {
    margin-left: 0.5rem;
  }
}
</style>
