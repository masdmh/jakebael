<template>
  <div :class="['xs-text-6 md-text-5 bael-grid', {paginated: hasPagination}]">
    <div v-if="posts.length" class="r full-height browse">
      <div
        v-intersect
        v-for="(p,i) in posts"
        :key="i"
        class="xs-border xs-border-top-none xs-border-left-none xs-p2 bcg-item"
        :style="`transition-delay:0.${i * .5}s`"
      >
		<div
          v-if="p.tile"
          class="item xs-block xs-full-height xs-flex xs-relative xs-flex-align-start xs-flex-justify-end xs-text-left"
        >
			<nuxt-link :to="p.path">
				<img v-lazy="p.tile" :key="p.tile"/>			
			</nuxt-link>
		</div>
        <div
          v-else
          class="item item-txt xs-block xs-full-height xs-flex xs-relative xs-flex-align-center xs-flex-justify-center xs-text-center"
        >
          <nuxt-link class="nobg-link" :to="p.path">{{p.title}}</nuxt-link>
        </div>
		
		
      </div>
    </div>
    <div v-else class="r full-height browse">
      <div class="xs-p2 c-100 xs-flex xs-flex-align-center xs-flex-justify-center xs-text-center">
        <div v-if="posts.length < 1 && !busy">No Results.</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    posts: {
      type: Array,
    },
  },
  data() {
    return {};
  },
  computed: {
    hasPagination() {
      return this.$store.state.pagination.active || false;
    },
  },
};
</script>

<style>
.bael-grid .bcg-item {
  opacity: 0;
  transition: 0.2s opacity ease-out;
}
.bael-grid .intersected.bcg-item {
  opacity: 1;
  transition: 0.2s opacity ease-out;
}
</style>
