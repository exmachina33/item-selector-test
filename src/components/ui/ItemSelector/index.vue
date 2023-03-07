<template>
  <div class="item-selector">
    <ItemCard
        v-for="(item, index) in items"
        :key="index"
        :item="item"
        :selected="findItem(item, value)"
        @click="selectItem(item)"
    />
  </div>
</template>

<script>
import ItemCard from "@/components/ui/ItemCard";
export default {
  name: "ItemSelector",
  components: {ItemCard},
  model: {
    prop: 'value',
    event: 'select'
  },
  props: {
    items: {
      type: Array,
      default: () => ([])
    },
    value: {
      type: [Array, Object, null],
      default: null
    },
    multiple: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    selectItem(item) {
      if(this.multiple) {
        this.updateMultipleValue(item)
        return
      }
      this.updateSingleValue(item)
    },
    updateMultipleValue(item) {
      if(this.value) {

        let items = Array.isArray(this.value) ? [...this.value] : [this.value];
        this.findItem(item, this.value) ? items = items.filter(i => i.id != item.id) : items.push(item);
        this.emitItems(items);
        return;
      }
      this.emitItems([item]);
    },
    updateSingleValue(item) {
      this.findItem(item, this.value) ? this.emitItems(null) : this.emitItems(item)
    },
    emitItems(item) {
      this.$emit('select', item);
    },
    findItem(item, selected) {
      /// ищем item среди выбранных по id
      if (!selected) return false;

      if (!Array.isArray(selected)) selected = [selected];
      for (let i = 0; i < selected.length; i++) {
        if (item.id === selected[i].id) {
          return true;
          break;
        }
      }
      return false
    },
  }
}
</script>

<style lang="scss" scoped>
.item-selector {
  display: flex;
  border: 2px solid #000;
  flex-wrap: wrap;
  gap: 20px;
  padding: 10px;
}
</style>