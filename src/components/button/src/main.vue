<template>
<button :disabled="disabled" @click="handleClick" :class="classes" :type="nativeType">
  <slot></slot>
</button>
</template>

<script>

  const prefixOfClass = 'mu-button';

  export default {
    name: "MuButton",
    props: {
      disabled: Boolean,
      nativeType: {
        default: 'button',
        validator (value) {
          return (['button', 'submit', 'reset'].indexOf(value) >= 0);
        }
      },
      long: Boolean
    },
    methods: {
      handleClick (event) {
        this.$emit('click', event);
      }
    },
    computed: {
      classes() {
        return [
          `${prefixOfClass}`,
          {
            [`${prefixOfClass}--long`]: this.long
          }
        ];
      }
    }
  }
</script>

<style scoped>

</style>
