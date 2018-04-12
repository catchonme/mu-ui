<template>
<button :disabled="disabled" @click="handleClick" :class="classes" :type="nativeType">
  <slot></slot>
</button>
</template>

<script>

  const prefixOfClass = 'mu-button';
  const elPrefixOfClass = 'el-button-';

  export default {
    name: "MuButton",
    props: {
      disabled: Boolean,
      nativeType: {
        type: String,
        default: 'button',
      },
      type:{
        type: String,
        default: 'default'
      },
      size: {
        type: String,
        default: 'medium'
      },
      plain: Boolean,
      round: Boolean,
      circle: Boolean
    },
    methods: {
      handleClick (event) {
        this.$emit('click', event);
      }
    },
    computed: {
      classes() {
        return [
          `${elPrefixOfClass}-${this.type}`,
          `${elPrefixOfClass}-${this.size}`,
          {
            'is-circle': this.circle,
            'is-plain': this.plain,
            'is-round': this.round,
          }
        ];
      }
    }
  }
</script>

<style scoped>

</style>
