<style lang="scss" scoped>
.text {
  color: #35d6c1;
}
</style>

<template>
  <div class="edit-mobile d-flex align-center">
    <div>
      <Icon :size="20" fileName="ic_edit.svg" />
    </div>
    <nuxt-link to="/patient/login" class="text mr-2">
      <span>ویرایش شماره</span>
      <span>{{ mobile }}</span>
    </nuxt-link>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'nuxt-property-decorator'
import Icon from '@/components/Common/Icon/Icon.vue'

@Component({
  components: {
    Icon,
  },
})
export default class EditMobile extends Vue {
  get mobile() {
    return this.$storage.getUniversal('login_mobile')
  }
}
</script>
