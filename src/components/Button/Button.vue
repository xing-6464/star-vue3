<template>
  <a
    v-if="(props.btnType === 'link' && props.href)"
    :class="classes"
    :href="props.href"
  >
  </a>
  <button
    v-else
    :disabled="props.disabled"
    :class="classes"
  >
  </button>
</template>

<script setup lang="ts">
import { defineProps, withDefaults } from 'vue'
import classNames from 'classnames'

type ButtonSize = 'lg' | 'sm'
type ButtonType = 'primary' | 'default' | 'danger' | 'link'

interface BaseButtonProps {
  className?: string
  href?: string
  disabled?: boolean
  size?: ButtonSize
  btnType?: ButtonType
}

const props = withDefaults(defineProps<BaseButtonProps>(), {
  btnType: 'default',
  disabled: false
})

const classes = classNames('btn', {
  [`btn-${props.btnType}`]: props.btnType,
  [`btn-${props.size}`]: props.size,
  disabled: (props.btnType === 'link') && props.disabled
})

</script>

<style lang="scss">

</style>
