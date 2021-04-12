<template>
  <div id="app" style="background-color: #eeeeee">
    <!-- <Row type="flex" justify="center">
      <Col span="8" style="height:160px;background-color:#f24;">col-8</Col>
  </Row> -->
    <br />
    <!-- 主體 -->
    <Row type="flex" justify="center">
      <Col :xs="16" :sm="12" style="max-width: 400px">
        <Layout>
          <Content :xs="24" :md="12">
            <Card class="Card" style="height: 480px">
              <h1 slot="title">歡迎</h1>
              <!-- <p slot="extra">預設admin</p> -->
              <Form
                ref="formValidate"
                :model="formValidate"
                :rules="ruleValidate"
                :label-width="80"
              >
                <FormItem class="radio" prop="switch_btn">
                  <RadioGroup v-model="formValidate.switch_btn">
                    <Radio label="a">帳戶登入</Radio>
                    <Radio label="b">信箱登入</Radio>
                  </RadioGroup>
                </FormItem>

                <FormItem
                  v-show="formValidate.switch_btn === 'a'"
                  label="帳戶"
                  prop="name"
                >
                  <Input
                    v-model="formValidate.name"
                    placeholder="admin"
                  ></Input>
                </FormItem>

                <FormItem
                  v-show="formValidate.switch_btn === 'b'"
                  label="信箱"
                  prop="email"
                >
                  <Input
                    v-model="formValidate.email"
                    placeholder="admin@gmail.com"
                  ></Input>
                </FormItem>

                <FormItem label="密碼" prop="password">
                  <Input
                    v-model="formValidate.password"
                    type="password"
                    placeholder="admin"
                  ></Input>
                </FormItem>

                <FormItem>
                  <Button type="primary" @click="handleSubmit(formValidate)"
                    >Submit</Button
                  >
                  <Button
                    @click="handleReset(formValidate)"
                    style="margin-left: 8px"
                    >Reset</Button
                  >
                </FormItem>
              </Form>
            </Card>
          </Content>
        </Layout>
      </Col>
    </Row>
  </div>
</template>

<script>
export default {
  data() {
    return {
      formValidate: {
        name: "",
        password: "",
        email: "",
        switch_btn: "a",
      },
      ruleValidate: {
        name: [{ required: true, message: "此項必填", trigger: "blur" }],
        email: [
          { required: true, message: "此項必填", trigger: "blur" },
          { type: "email", message: "Incorrect email format", trigger: "blur" },
        ],
        password: [{ required: true, message: "此項必填", trigger: "blur" }],
      },
    };
  },
  methods: {
    handleSubmit(value) {
      console.log(JSON.parse(JSON.stringify(value)));

      let { name, password, email } = JSON.parse(JSON.stringify(value));
      // login_api({ username: name, password });

      // console.log(account, password, email)
      if (name === "admin" && password === "admin") {
        console.log(alert("登入成功!"));
        this.$Message.success("登入成功!");
      } else if (email === "admin@gmail.com" && password === "admin") {
        console.log(alert("登入成功!"));
        this.$Message.success("登入成功!");
      } else {
        this.$Message.error("驗證失敗!");
        console.log(alert("驗證失敗!"));
      }
    },
    // handleSubmit (value) {
    //     this.$refs[value].validate((valid) => {
    //         if (valid==="Admin"  ) {
    //             this.$Message.success('已送出!');
    //         } else {
    //             this.$Message.error('已送出!');
    //         }
    //     })
    // },
    handleReset(name) {
      this.$refs[name].resetFields();
    },
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
<style lang="less" scoped>
.Card {
  border-radius: 30px;
  justify-content: center;
  box-shadow: 5px 5px 5px 1px rgba(0, 0, 0, 0.2);
  h1 {
    margin: 5px;
  }
}
.form {
  padding: 5px;
}
.radio {
  right: 0px;
  transform: translateX(-30px);
}
.table {
  background-color: #f24;
}
</style>
