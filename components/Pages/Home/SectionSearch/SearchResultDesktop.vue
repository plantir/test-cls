<style lang="scss" scoped></style>

<template>
  <section>
    <SearchResultItem
      v-if="result.doctors"
      :data="result.doctors"
      type="doctor"
      title="نتایج از بین پزشکان"
      :link="'/'"
    />
    <SearchResultItem
      v-if="result.specialities"
      :data="result.specialities"
      type="specialty"
      title="نتایج از بین تخصص ها"
      :link="'/'"
    />
    <SearchResultItem
      v-if="result.categories"
      :data="result.categories"
      type="illness"
      title="نتایج از بین بیماری ها"
      :link="'/'"
    />
  </section>
</template>

<script lang="ts">
import { Component, Vue, Prop, Watch } from 'nuxt-property-decorator'
import SearchResultItem from './SearchResultItemDesktop.vue'
@Component({
  components: {
    SearchResultItem,
  },
})
export default class SearchResult extends Vue {
  @Prop({
    type: Object,
    required: true,
  })
  readonly result!: object

  @Watch('result', { deep: true })
  onResultChange() {}
}
</script>
