<template>
  <div>
    <Card class="bg-gray-100 pb-0 mb-10">
      <h1 class="font-medium mb-5 text-gray-600 text-lg">
        Login to your account
      </h1>
      <form @submit.prevent="submit" class="border-t border-gray-200 -mx-10">
        <FormGroup
          placeholder="Email Address"
          icon-name="mail"
          icon-type="ionicon"
        />
        <FormGroup
          type="password"
          placeholder="Password"
          icon-name="lock-closed"
          icon-type="ionicon"
        />
        <FormGroup
          type="checkbox"
          label="Keep me logged in"
        />
        <button
          type="submit"
          class="duration-300 flex font-medium h-15 items-center pr-10 py-4 rounded-bl-xl rounded-br-xl text-left text-sm w-full  disabled:cursor-not-allowed"
          :class="{
            'bg-blue-700 text-white hover:bg-blue-700 focus:bg-blue-700': loading,
            'bg-green-500 text-white hover:bg-green-500 focus:bg-green-500': success,
            'bg-blue-500 text-white hover:bg-blue-400 focus:bg-blue-600 focus:outline-none': !loading && !success
          }"
          :disabled="loading || success"
        >
          <span class="flex items-center mr-3 max-w-24 min-w-24 pr-6 pl-10 w-24 text-2xl">
            <Spinner v-if="loading" />
            <ion-icon v-else-if="success" name="checkmark-done" />
            <ion-icon v-else name="log-in" />
          </span>
          <template>
            <span v-if="loading">
              Authenticating...
            </span>
            <span v-else-if="success">
              Authentication successful!
            </span>
            <span v-else>
              Access Account
            </span>
          </template>
        </button>
      </form>
    </Card>
    <div>
      <Link to="/register">Create Account Instead</Link>
    </div>
  </div>
</template>

<script>
export default {
  head: {
    title: 'Login to 2020'
  },
  layout: 'authentication',
  data () {
    return {
      loading: false,
      success: false
    }
  },
  methods: {
    submit () {
      if (this.loading || this.success) {
        return
      }

      this.loading = true;

      setTimeout(() => {
        this.loading = false;
        this.success = true;
      }, 2000);

      setTimeout(() => {
        this.success = false;
      }, 4000);
    }
  }
}
</script>
