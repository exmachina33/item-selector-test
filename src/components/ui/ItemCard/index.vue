<template>
  <div v-if="item" @click="clickHandler" :class="classes">
    <span v-text="item.name"/>
    <span v-text="item.id"/>
  </div>
</template>

<script>
export default {
  name: "ItemCard",
  props: {
    item: {
      type: Object,
      default: () => {}
    },
    size: {
      type: String,
      default: 'medium'
    },
    selected: {
      type: Boolean,
      default: false
    }
  },
  computed: {
    classes() {
      const classes = ['item-card'];
      classes.push(`item-card--${this.size}`);
      if(this.selected) classes.push('item-card--selected')
      return classes
    }
  },
  methods: {
    clickHandler(event) {
      this.$emit('click', event)
    }
  }
}
</script>

<style lang="scss" scoped>
.item-card {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 5px;
  border: 1px solid #000;
  cursor: pointer;

  &--medium {
    width: 60px;
    height: 60px;
  }
  &--fill {
    width: 100%;
    height: 100%;
  }
  &--selected {
    border-color: #41d971
  }
}
</style>