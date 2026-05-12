<template>
  <button
    :type="type"
    :disabled="disabled || loading"
    :class="classes"
    v-bind="$attrs"
  >
    <span v-if="loading" class="inline-block w-4 h-4 border-2 border-current border-t-transparent rounded-full animate-spin" />
    <span v-if="iconLeft && !loading" class="text-base leading-none">{{ iconLeft }}</span>
    <span><slot /></span>
    <span v-if="iconRight && !loading" class="text-base leading-none">{{ iconRight }}</span>
  </button>
</template>

<script setup lang="ts">
import { computed } from 'vue'

type Variant = 'primary' | 'outline' | 'ghost' | 'danger' | 'secondary' | 'gold'
type Size    = 'sm' | 'md' | 'lg'

const props = withDefaults(defineProps<{
  variant?:   Variant
  size?:      Size
  type?:      'button' | 'submit' | 'reset'
  disabled?:  boolean
  loading?:   boolean
  iconLeft?:  string
  iconRight?: string
  full?:      boolean
}>(), {
  variant:  'primary',
  size:     'md',
  type:     'button',
  disabled: false,
  loading:  false,
  full:     false,
})

const base = [
  'inline-flex items-center justify-center gap-2 font-sans font-semibold rounded-xl',
  'transition-all duration-200 focus:outline-none focus-visible:ring-2 focus-visible:ring-offset-2 active:scale-95',
  'disabled:opacity-50 disabled:cursor-not-allowed disabled:scale-100',
]

const variants: Record<Variant, string> = {
  primary:   'bg-brand-500 hover:bg-brand-600 text-white shadow-warm-sm hover:shadow-warm-md focus-visible:ring-brand-400 focus-visible:ring-offset-stone-50',
  outline:   'border-2 border-brand-500 text-brand-600 hover:bg-brand-50 focus-visible:ring-brand-400 focus-visible:ring-offset-stone-50',
  ghost:     'text-stone-600 hover:text-stone-900 hover:bg-stone-100 focus-visible:ring-stone-300 focus-visible:ring-offset-stone-50',
  secondary: 'bg-stone-100 hover:bg-stone-200 text-stone-800 focus-visible:ring-stone-300 focus-visible:ring-offset-stone-50',
  danger:    'bg-blush-500 hover:bg-blush-400 text-white shadow-sm focus-visible:ring-blush-400 focus-visible:ring-offset-stone-50',
  gold:      'bg-gold-400 hover:bg-gold-500 text-stone-900 shadow-warm-sm hover:shadow-warm-md focus-visible:ring-gold-400 focus-visible:ring-offset-stone-50',
}

const sizes: Record<Size, string> = {
  sm: 'px-4 py-1.5 text-sm',
  md: 'px-5 py-2.5 text-sm',
  lg: 'px-8 py-3.5 text-base tracking-wide',
}

const classes = computed(() => [
  ...base,
  variants[props.variant],
  sizes[props.size],
  props.full ? 'w-full' : '',
])
</script>
