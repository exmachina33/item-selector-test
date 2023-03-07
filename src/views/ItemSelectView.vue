<template>
  <div class="item-select-view">
    <div class="item-select-view__multiple">
      <div class="item-select-view__multiple__selected">
        <ItemCard v-for="(item, index) in multipleSelected" :key="index" :item="item"/>
      </div>
      <ItemSelector :items="multipleList" v-model="multipleValue" multiple/>
    </div>
    <div class="item-select-view__single">
      <div class="item-select-view__single__selected">
        <ItemCard :item="singleValue" size="fill"/>
      </div>
      <ItemSelector :items="singleList" v-model="singleValue"/>
    </div>
  </div>
</template>

<script>
import ItemSelector from "@/components/ui/ItemSelector";
import ItemCard from "@/components/ui/ItemCard";
export default {
  name: "ItemSelectView",
  components: {ItemCard, ItemSelector},
  data() {
    return {
      multipleValue: null,
      singleValue: null,
      multipleList: [
        {
          "id": 1,
          "name": "Shoes 1"
        },
        {
          "id": 2,
          "name": "Shoes 2"
        },
        {
          "id": 3,
          "name": "Shoes 3"
        },
        {
          "id": 4,
          "name": "Shoes 4"
        },
        {
          "id": 5,
          "name": "T-shirt 1"
        },
        {
          "id": 6,
          "name": "T-shirt 2"
        },
        {
          "id": 7,
          "name": "T-shirt 3"
        },
        {
          "id": 8,
          "name": "T-shirt 4"
        }
      ],
      singleList: [
        {
          "id": 11,
          "name": "Jacket 1"
        },
        {
          "id": 12,
          "name": "Jacket 2"
        },
        {
          "id": 13,
          "name": "Jacket 3"
        },
        {
          "id": 14,
          "name": "Jacket 4"
        },
        {
          "id": 15,
          "name": "Hoodie 1"
        },
        {
          "id": 16,
          "name": "Hoodie 2"
        },
        {
          "id": 17,
          "name": "Hoodie 3"
        },
        {
          "id": 18,
          "name": "Hoodie 4"
        }
      ]
    }
  },
  computed: {
    multipleSelected() {
      return Array.isArray(this.multipleValue) ? this.multipleValue : [this.multipleValue]
    }
  }
}
</script>

<style lang="scss" scoped>
.item-select-view {
  display: flex;
  gap: 20px;
  padding: 20px;

  &__multiple {
    display: flex;
    flex-direction: column;
    gap: 20px;

    &__selected {
      min-width: 160px;
      min-height: 160px;
      width: fit-content;
      border: 2px solid #000;
      display: flex;
      gap: 20px;
      padding: 10px;
      flex-wrap: wrap;
    }
  }

  &__single {
    display: flex;
    flex-direction: column;
    gap: 20px;
    align-items: flex-end;

    &__selected {
      min-width: 160px;
      min-height: 160px;
      width: fit-content;
      border: 2px solid #000;
      display: flex;
      gap: 20px;
      padding: 10px;
      flex-wrap: wrap;
    }
  }
}
</style>