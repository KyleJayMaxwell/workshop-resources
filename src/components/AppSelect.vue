<template>
  <AppDropdown>
    <!-- Your code here -->
    <slot name="selected"/>
    <template #content="{ isOpen, setIsOpen }">
      <ul>
        <li v-for="(option, index) in options"
          :key="index" @click="update(option, setIsOpen)">
          <slot name="option" v-bind="{ option, isOpen, setIsOpen}"/>
        </li>
      </ul>
    </template>
  </AppDropdown>
</template>

<script>
import AppDropdown from './AppDropdown'

export default {
  components: {
    AppDropdown
  },
  props: {
    options: {
      type: Array
    },
    value: {
      type: [String, Object]
    }
  },
  methods: {
    update (option, cb) {
      this.$emit('input', option)
      if (cb) cb()
    }
  }
}
</script>

<style lang="sass" scoped>
ul
  list-style: none
  padding: 0
  margin: -10px

  li
    border-bottom: 1px solid #f0f0f0
    padding: 8px 14px
    cursor: pointer

    &:hover
      background: #f0f0f0
</style>
