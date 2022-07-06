<template>
  <div class="size-name" v-if="isSelected">
    <slot></slot>
  </div>
</template>
<script>
export default {
  props: {
    isSelected: {
      type: Boolean,
    },
  },
}
</script>

<style lang="scss" scoped>
.size-name {
    display: block;
    font-size: 16px;
    line-height: 19px;
    display: flex;
    align-items: center;
    color: #626262;
}
</style>