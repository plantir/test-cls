<style lang="scss" scoped>
form {
  width: 100%;
  ::v-deep {
    .v-input {
      width: 100%;
      .v-input__slot {
        background: #fff;
      }
    }
    .v-label {
      color: #4b4b4b;
    }
    button {
      width: 100% !important;
      display: block;
    }
  }
  @include media(sm) {
    width: 370px;
    ::v-deep {
      button {
        width: 70% !important;
        display: block;
      }
    }
  }
  .resaa-btn {
    height: 48px !important;
    @include media(sm) {
      height: 56px !important;
    }
  }
}
</style>

<template>
  <form @submit.prevent="onSubmit" class="d-flex flex-column align-center">
    <!--     v-validate="'required'"
      :error-messages="errors.collect('q')"
      data-vv-as="نام و نام خانوادگی، تخصص، بیماری" -->
    <v-text-field
      :loading="loading"
      v-model="value"
      label="نام و نام خانوادگی، تخصص، بیماری"
      name="q"
      @input="onChange"
      outlined
      clearable
    >
      <template v-slot:append>
        <img
          width="30"
          height="30"
          src="/images/icons/ic_search.png"
          alt="search"
        />
      </template>
    </v-text-field>

    <v-btn class="resaa-btn" @click="onSubmit" large>جستجو در رسا</v-btn>
  </form>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'nuxt-property-decorator'

@Component
export default class SearchForm extends Vue {
  value = ''
  @Prop()
  loading!: boolean
  onSubmit() {
    if (this.value && this.value != '') {
      this.$emit('submit', this.value)
    }
  }

  onChange() {}
}
</script>
