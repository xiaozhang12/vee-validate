<template>
  <ValidationObserver v-slot="{ invalid }">
    <form @submit.prevent="onSubmit">
      <ValidationProvider name="E-mail" rules="required|email" v-slot="{ errors }">
        <input v-model="email" type="email">
        <span>{{ errors[0] }}</span>
      </ValidationProvider>

      <ValidationProvider name="First Name" rules="required|alpha" v-slot="{ errors }">
        <input v-model="firstName" type="text">
        <span>{{ errors[0] }}</span>
      </ValidationProvider>

      <ValidationProvider name="Last Name" rules="required|alpha" v-slot="{ errors }">
        <input v-model="lastName" type="text">
        <span>{{ errors[0] }}</span>
      </ValidationProvider>

      <button type="submit" :disabled="invalid">Submit</button>
    </form>
  </ValidationObserver>
</template>

<script>
export default {
  data: () => ({
    email: '',
    firstName: '',
    lastName: ''
  }),
  methods: {
    onSubmit () {
      alert('Form has been submitted!');
    }
  }
};
</script>

<style lang="stylus" scoped>
span {
  display: block;
}
</style>
