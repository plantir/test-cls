<style lang="scss" scoped>
.filter-based {
  .top {
    .label {
      font-size: 14px;
      font-weight: bold;
    }
  }
  .bottom {
    color: $primary-color;
    button {
      margin-left: 10px;
      font-size: 14px;
      font-weight: bold;
      &:last-child {
        margin-left: 0;
      }
      i {
        font-size: 24px;
      }
    }
  }
}
</style>

<template>
  <div class="filter-based">
    <div class="top d-flex align-center justify-space-between">
      <span class="label">فیلتر بر اساس:</span>
      <div class="left d-flex">
        <FilterBySpecialty
          :specialities="specialities"
          v-model="filter.specialty"
          @input="onSubmit"
        />
        <FilterBySickness
          :categories="categories"
          v-model="filter.sickness"
          @input="onSubmit"
          class="mr-3"
        />
      </div>
    </div>
    <div class="bottom d-flex align-start mt-5">
      <button
        v-if="filter.specialty.length > 0"
        type="button"
        class="d-flex align-center"
        @click="onRemoveFilterSpecialty"
      >
        <i class="las la-times-circle"></i>
        <span class="label mr-2">حذف فیلتر تخصص</span>
      </button>
      <button
        v-if="filter.sickness.length > 0"
        type="button"
        class="d-flex align-center"
        @click="onRemoveFilterSickness"
      >
        <i class="las la-times-circle"></i>
        <span class="label mr-2">حذف فیلتر یبماری</span>
      </button>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue, Prop } from 'nuxt-property-decorator'
import FilterBySpecialty from './FilterBySpecialty/FilterBySpecialty.vue'
import FilterBySickness from './FilterBySickness/FilterBySickness.vue'

@Component({
  components: {
    FilterBySpecialty,
    FilterBySickness,
  },
})
export default class FilterBased extends Vue {
  @Prop({
    type: Object,
    required: true,
  })
  readonly value!: { specialty: any[]; sickness: any[] }

  get filter() {
    return this.value
  }

  set filter(val) {
    // this.$emit('input', val)
  }
  @Prop()
  categories!: any[]

  @Prop()
  specialities!: any[]

  onRemoveFilterSpecialty() {
    this.filter.specialty = []
    this.onSubmit()
  }

  onRemoveFilterSickness() {
    this.filter.sickness = []
    this.onSubmit()
  }

  onSubmit() {
    this.$emit('input', this.filter)
    this.$emit('submit')
  }
}
</script>
