<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div>
  {{ user }}
  <Form @submit="onSubmit" v-slot="{ errors }">
    <div class="mb-3">
      <label for="email" class="form-label">Email</label>
      <Field id="email" name="email" type="email" class="form-control"
      :class="{ 'is-invalid': errors['email'] }" placeholder="請輸入 Email"
      rules="email|required" v-model="user.email"></Field>
      <ErrorMessage name="email" class="invalid-feedback"></ErrorMessage>
    </div>
    <div class="mb-3">
      <label for="name" class="form-label">Name</label>
      <Field id="name" name="姓名" type="text" class="form-control"
      :class="{ 'is-invalid': errors['姓名'] }" placeholder="請輸入姓名"
      rules="required" v-model="user.name"></Field>
      <ErrorMessage name="姓名" class="invalid-feedback"></ErrorMessage>
    </div>
    <div class="mb-3">
      <label for="phone" class="form-label">電話</label>
      <Field id="phone" name="電話" type="text" class="form-control"
      :class="{ 'is-invalid': errors['電話'] }" placeholder="請輸入電話"
      :rules="isPhone" v-model="user.phone"></Field>
      <ErrorMessage name="電話" class="invalid-feedback"></ErrorMessage>
    </div>
    <div class="mb-3">
      <label for="region" class="form-label">地區</label>
      <Field id="region" name="地區" class="form-control"
      :class="{ 'is-invalid': errors['地區'] }"  placeholder="請輸入地區"
      rules="required" v-model="user.region" as="select">
        <option value="">請選擇地區</option>
        <option value="台北市">台北市</option>
        <option value="高雄市">高雄市</option>
      </Field>
      <ErrorMessage name="地區" class="invalid-feedback"></ErrorMessage>
    </div>
    <div class="mb-3">
      <label for="address" class="form-label">地址</label>
      <Field id="address" name="地址" type="text" class="form-control"
      :class="{ 'is-invalid': errors['地址'] }" placeholder="請輸入地址"
      rules="required" v-model="user.address"></Field>
      <ErrorMessage name="地址" class="invalid-feedback"></ErrorMessage>
    </div>
    <button class="btn btn-primary" type="submit">Submit</button>
  </Form>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue';

export default {
  name: 'HomeView',
  components: {
    HelloWorld,
  },
  data() {
    return {
      user: {
        email: '',
        name: '',
        address: '',
        phone: '',
      },
    };
  },
  methods: {
    onSubmit() {
      console.log(this.user);
    },
    isPhone(value) {
      const phoneNumber = /^(09)[0-9]{8}$/;
      return phoneNumber.test(value) ? true : '需要正確的電話號碼';
    },
  },
  created() {
    console.log(this);
  },
};
</script>
