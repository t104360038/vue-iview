<template>
  <Form
    ref="formValidate"
    :model="formValidate"
    :rules="ruleValidate"
    :label-width="80"
  >
    <FormItem label="姓名" prop="name">
      <Input v-model="formValidate.name" placeholder="Enter your name"></Input>
    </FormItem>
    <FormItem label="信箱" prop="mail">
      <Input
        v-model="formValidate.mail"
        placeholder="Enter your e-mail"
      ></Input>
    </FormItem>
    <FormItem label="地區" prop="city">
      <Select v-model="formValidate.city" placeholder="選擇城市">
        <Option value="beijing">台北</Option>
        <Option value="shanghai">台中</Option>
        <Option value="shenzhen">高雄</Option>
      </Select>
    </FormItem>
    <FormItem label="密碼" prop="passwd">
      <Input type="password" v-model="formValidate.passwd"></Input>
    </FormItem>
    <FormItem label="確認密碼" prop="passwdCheck">
      <Input type="password" v-model="formValidate.passwdCheck"></Input>
    </FormItem>
    <FormItem label="年齡" prop="age">
      <Input type="text" v-model="formValidate.age" number></Input>
    </FormItem>
    <FormItem label="開通日期">
      <Row>
        <Col span="11">
          <FormItem prop="date">
            <DatePicker
              type="date"
              placeholder="Select date"
              v-model="formValidate.date"
            ></DatePicker>
          </FormItem>
        </Col>
        <Col span="2" style="text-align: center">-</Col>
        <Col span="11">
          <!-- <FormItem prop="time">
                        <TimePicker type="time" placeholder="Select time" v-model="formValidate.time"></TimePicker>
                    </FormItem> -->
        </Col>
      </Row>
    </FormItem>
    <FormItem label="方案" prop="gender">
      <RadioGroup v-model="formValidate.gender">
        <Radio label="快速">快速</Radio>
        <Radio label="一般">一般</Radio>
      </RadioGroup>
    </FormItem>
    <FormItem label="額外服務" prop="interest">
      <CheckboxGroup v-model="formValidate.interest">
        <Checkbox label="送禮包裝"></Checkbox>
        <Checkbox label="一般包裝"></Checkbox>
        <Checkbox label="保護膜"></Checkbox>
        <Checkbox label="手提袋"></Checkbox>
      </CheckboxGroup>
    </FormItem>
    <FormItem label="其他" prop="desc">
      <Input
        v-model="formValidate.desc"
        type="textarea"
        :autosize="{ minRows: 2, maxRows: 5 }"
        placeholder="Enter something..."
      ></Input>
    </FormItem>
    <FormItem>
      <Button type="primary" @click="handleSubmit('formValidate')"
        >Submit</Button
      >
      <Button @click="handleReset('formValidate')" style="margin-left: 8px"
        >Reset</Button
      >
    </FormItem>
  </Form>
</template>
<script>
export default {
  data() {
    const validatePass = (rule, value, callback) => {
      if (value === "") {
        callback(new Error("請輸入密碼"));
      } else {
        if (this.formValidate.passwdCheck !== "") {
          // 对第二个密码框单独验证
          this.$refs.formValidate.validateField("passwdCheck");
        }
        callback();
      }
    };
    const validatePassCheck = (rule, value, callback) => {
      if (value === "") {
        callback(new Error("請再次輸入密碼"));
      } else if (value !== this.formValidate.passwd) {
        callback(new Error("輸入密碼未相符!"));
      } else {
        callback();
      }
    };
    const validateAge = (rule, value, callback) => {
      if (!value) {
        return callback(new Error("請輸入年紀"));
      }
      // 模拟异步验证效果
      setTimeout(() => {
        if (!Number.isInteger(value)) {
          callback(new Error("Please enter a numeric value"));
        } else {
          if (value < 18) {
            callback(new Error("Must be over 18 years of age"));
          } else {
            callback();
          }
        }
      }, 1000);
    };

    return {
      formValidate: {
        name: "",
        mail: "",
        city: "",
        gender: "",
        interest: [],
        date: "",
        time: "",
        desc: "",
        passwd: "",
        passwdCheck: "",
        age: "",
      },
      ruleValidate: {
        name: [{ required: true, message: "請輸入密碼", trigger: "blur" }],
        mail: [
          { required: true, message: "請輸入信箱", trigger: "blur" },
          { type: "email", message: "非信箱格式", trigger: "blur" },
        ],
        city: [{ required: true, message: "請輸入城市", trigger: "change" }],
        gender: [{ required: true, message: "請輸入方案r", trigger: "change" }],
        // interest: [
        //     { required: true, type: 'array', min: 1, message: 'Choose at least one hobby', trigger: 'change' },
        //     { type: 'array', max: 2, message: 'Choose two hobbies at best', trigger: 'change' }
        // ],
        date: [
          {
            required: true,
            type: "date",
            message: "請輸入日期",
            trigger: "change",
          },
        ],
        // time: [
        //     { required: true, type: 'string', message: 'Please select time', trigger: 'change' }
        // ],
        // desc: [
        //     { required: true, message: 'Please enter a personal introduction', trigger: 'blur' },
        //     { type: 'string', min: 0, message: 'Introduce no less than 20 words', trigger: 'blur' }
        // ],
        passwd: [{ validator: validatePass, trigger: "blur" }],
        passwdCheck: [{ validator: validatePassCheck, trigger: "blur" }],
        age: [{ validator: validateAge, trigger: "blur" }],
      },
    };
  },
  methods: {
    handleSubmit(name) {
      this.$refs[name].validate((valid) => {
        if (valid) {
          this.$Message.success("Success!");
        } else {
          this.$Message.error("Fail!");
        }
      });
    },
    handleReset(name) {
      this.$refs[name].resetFields();
    },
  },
};
</script>
