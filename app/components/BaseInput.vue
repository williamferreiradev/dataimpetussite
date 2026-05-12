<template>
  <div :class="['flex flex-col gap-1', props.full ? 'w-full' : 'w-fit']">

    <!-- Label -->
    <label
      v-if="label"
      :for="inputId"
      class="text-sm font-medium text-stone-700"
    >
      {{ label }}
      <span v-if="required" class="text-rose-400 ml-0.5">*</span>
    </label>

    <!-- Input wrapper -->
    <div class="relative flex items-center">

      <!-- Ícone à esquerda -->
      <span
        v-if="iconLeft"
        class="absolute left-3 text-stone-400 pointer-events-none select-none text-base"
      >
        {{ iconLeft }}
      </span>

      <!-- Input / Textarea -->
      <component
        :is="type === 'textarea' ? 'textarea' : 'input'"
        :id="inputId"
        v-model="model"
        :type="type !== 'textarea' ? resolvedType : undefined"
        :placeholder="placeholder"
        :disabled="disabled"
        :readonly="readonly"
        :rows="type === 'textarea' ? rows : undefined"
        :class="inputClasses"
        v-bind="$attrs"
        @focus="focused = true"
        @blur="focused = false"
      />

      <!-- Toggle de senha -->
      <button
        v-if="type === 'password'"
        type="button"
        class="absolute right-3 text-stone-400 hover:text-stone-600 transition-colors text-base"
        @click="showPassword = !showPassword"
      >
        {{ showPassword ? '🙈' : '👁️' }}
      </button>

      <!-- Ícone à direita -->
      <span
        v-else-if="iconRight"
        class="absolute right-3 text-stone-400 pointer-events-none select-none text-base"
      >
        {{ iconRight }}
      </span>
    </div>

    <!-- Hint / Erro -->
    <p v-if="error" class="text-xs text-rose-500 flex items-center gap-1 mt-0.5">
      <span>⚠</span> {{ error }}
    </p>
    <p v-else-if="hint" class="text-xs text-stone-400 mt-0.5">
      {{ hint }}
    </p>
  </div>
</template>

<script setup lang="ts">
import { computed, ref } from 'vue'

type InputType = 'text' | 'email' | 'password' | 'number' | 'tel' | 'url' | 'search' | 'textarea'
type InputSize = 'sm' | 'md' | 'lg'

const props = withDefaults(defineProps<{
  modelValue?:  string | number
  label?:       string
  placeholder?: string
  type?:        InputType
  size?:        InputSize
  disabled?:    boolean
  readonly?:    boolean
  required?:    boolean
  error?:       string
  hint?:        string
  iconLeft?:    string
  iconRight?:   string
  full?:        boolean
  rows?:        number
  id?:          string
}>(), {
  type:     'text',
  size:     'md',
  disabled: false,
  readonly: false,
  required: false,
  full:     true,
  rows:     4,
})

const emit = defineEmits<{ 'update:modelValue': [value: string | number] }>()

const model = computed({
  get: () => props.modelValue,
  set: (val) => emit('update:modelValue', val as string | number),
})

const showPassword = ref(false)
const focused      = ref(false)

const inputId = computed(() => props.id ?? `input-${Math.random().toString(36).slice(2, 9)}`)

const resolvedType = computed(() => {
  if (props.type === 'password') return showPassword.value ? 'text' : 'password'
  return props.type
})

const sizes: Record<InputSize, string> = {
  sm: 'py-1.5 text-sm',
  md: 'py-2.5 text-sm',
  lg: 'py-3.5 text-base',
}

const inputClasses = computed(() => {
  const hasIconLeft  = !!props.iconLeft
  const hasIconRight = !!props.iconRight || props.type === 'password'

  return [
    // Base — tema light
    'w-full bg-white border rounded-xl text-stone-900 placeholder-stone-400',
    'transition-all duration-200 outline-none font-sans',
    'disabled:opacity-50 disabled:cursor-not-allowed disabled:bg-stone-50',
    sizes[props.size],
    hasIconLeft  ? 'pl-10' : 'pl-4',
    hasIconRight ? 'pr-10' : 'pr-4',
    // Estado de borda
    props.error
      ? 'border-rose-400 focus:border-rose-400 ring-2 ring-rose-400/20'
      : focused.value
        ? 'border-brand-400 ring-2 ring-brand-400/20'
        : 'border-stone-200 hover:border-stone-300',
    props.type === 'textarea' ? 'resize-y min-h-[100px]' : '',
  ]
})
</script>
