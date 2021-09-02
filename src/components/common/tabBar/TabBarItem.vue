<template>
  <div class="item" @click="itemClick">
    <div v-if="activeClick"><slot name="item-img"></slot></div>
    <div v-else><slot name="item-img-active"></slot></div>
    <div :class="{ active: !activeClick }"><slot name="item-text"></slot></div>
  </div>
</template>

<script>
export default {
  name: "TabBarItem",
  props: {
    path: String,
  },
  data() {
    return {
      isActive: true,
    };
  },
  computed: {
    activeClick() {
      console.log(this.$route.path);
      return this.$route.path.indexOf(this.path);
    },
  },
  methods: {
    itemClick() {
      this.$router.replace(this.path);
    },
  },
};
</script>

<style>
.item {
  flex: 1;
  text-align: center;
  height: 49px;
  font-size: 14px;
}

.item img {
  width: 24px;
  height: 24px;
  margin-top: 3px;
  vertical-align: middle;
  margin-bottom: 2px;
}

.active {
  color: red;
}
</style>