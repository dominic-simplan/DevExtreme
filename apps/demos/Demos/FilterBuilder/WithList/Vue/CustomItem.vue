<template>
  <div>
    <div class="product">
      <img
        :src="item.ImageSrc"
        :alt="'Picture of {{item.Name}}'"
      >
      <div>{{ item.Name }}</div>
      <div class="price">{{ currency(item.Price) }}</div>
    </div>
  </div>
</template>
<script setup lang="ts">
withDefaults(defineProps<{
  item?: Record<string, any>
}>(), {
  item: () => ({}),
});

const currencyFormatter = new Intl.NumberFormat('en-US', {
  style: 'currency',
  currency: 'USD',
  minimumFractionDigits: 0,
  maximumFractionDigits: 0,
});

const currency = (data) => currencyFormatter.format(data);
</script>
<style scoped>
.product {
  height: 65px;
}

.product > img {
  height: 100%;
  float: left;
}

.product > div {
  padding-left: 10px;
  vertical-align: top;
  line-height: 65px;
  font-size: 15px;
  float: left;
}

.product > div.price {
  float: right;
  font-size: 18px;
}
</style>
