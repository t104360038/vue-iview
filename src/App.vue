<!--<template>
  <div id="app" style="background:#eeeeee;">
    <div id="nav">
      <router-link to="/">Home</router-link>
      <br>
      <router-link to="/login">login</router-link>
      <br>
      <router-link to="/about">About</router-link>
      <router-link to="/text">Text</router-link>
    </div>
    <router-view></router-view>
  </div>
</template>-->

<template>
  <div class="layout">
    <Layout>
      <Header>
        <Menu mode="horizontal" theme="Primary" active-name="1">
          <div class="layout-logo1"></div>
          <div class="layout-nav">
            <MenuItem name="1">
              <Icon type="ios-paper"></Icon>
              <router-link to="/todo">今日待辦</router-link>
            </MenuItem>
            <MenuItem name="2">
              <Icon type="ios-keypad"></Icon>
              <router-link to="/login">登入</router-link>
            </MenuItem>
            <MenuItem name="3">
              <Icon type="ios-analytics"></Icon>
              <router-link to="/About">服務</router-link>
            </MenuItem>
            <MenuItem name="4">
              <Icon type="ios-paper"></Icon>
              <router-link to="/registered">註冊</router-link>
            </MenuItem>
            <!-- <MenuItem name="5">
                            <Icon type="ios-paper"></Icon>
                            <router-link to="/home">home</router-link>
                        </MenuItem> -->
          </div>
        </Menu>
      </Header>
      <Layout style="height: 90vh" theme="light">
        <Sider
          breakpoint="md"
          ref="side1"
          hide-trigger
          collapsible
          :collapsed-width="0"
          v-model="isCollapsed"
        >
          <Menu active-name="1-2" theme="dark" width="auto" :open-names="['0']">
            <Submenu name="1">
              <template slot="title">
                <Icon type="ios-navigate"></Icon>
                總公司
              </template>
              <MenuItem name="1-1"
                ><router-link to="/About">服務</router-link></MenuItem
              >
              <MenuItem name="1-2"
                ><router-link to="/registered">註冊</router-link></MenuItem
              >
              <MenuItem name="1-3"
                ><router-link to="/todo">今日待辦</router-link></MenuItem
              >
            </Submenu>
            <Submenu name="2">
              <template slot="title">
                <Icon type="ios-keypad"></Icon>
                季節活動
              </template>
              <MenuItem name="2-1"
                ><router-link to="/text">活動快報</router-link></MenuItem
              >
              <MenuItem name="2-2">Option 2</MenuItem>
            </Submenu>
            <Submenu name="3">
              <template slot="title">
                <Icon type="ios-analytics"></Icon>
                Item 3
              </template>
              <MenuItem name="3-1">Option 1</MenuItem>
              <MenuItem name="3-2">Option 2</MenuItem>
            </Submenu>
          </Menu>
        </Sider>
        <Layout>
          <Header :style="{ padding: 0 }" class="layout-header-bar">
            <Icon
              @click.native="collapsedSider"
              :class="rotateIcon"
              :style="{ margin: '0 20px' }"
              type="md-menu"
              size="24"
            ></Icon>
          </Header>
          <Content
            :style="{ padding: '24px', minHeight: '280px', background: '#fff' }"
          >
            <router-view></router-view>
          </Content>
        </Layout>
      </Layout>
      <Layout>
        <Footer :style="{ background: '#fff' }">
          台灣 © 2021 Poming-text, Inc. All Rights Reserved 指南 銷售條款
          使用條款 Poming
          <a
            href="https://agreementservice.svs.nike.com/tw/zh_tw/rest/agreement?agreementType=privacyPolicy&uxId=com.nike.commerce.nikedotcom.web&country=TW&language=zh&requestType=redirect"
            target="_blank"
            >隱私權政策</a
          >
        </Footer>
      </Layout>
    </Layout>
  </div>
</template>

//
<script>
// import HelloWorld from './components/HelloWorld.vue'

// export default {
//   name: 'app',
//   components: {
//     HelloWorld
//   }
// }
//
</script>
<script>
export default {
  data() {
    return {
      isCollapsed: false,
    };
  },
  computed: {
    rotateIcon() {
      return ["menu-icon", this.isCollapsed ? "rotate-icon" : ""];
    },
    menuitemClasses() {
      return ["menu-item", this.isCollapsed ? "collapsed-menu" : ""];
    },
  },
  methods: {
    collapsedSider() {
      this.$refs.side1.toggleCollapse();
    },
  },
};
</script>

<style>
#app {
  font-family: "微軟正黑體", "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 0px;
}
</style>

<style scoped>
.layout-logo1 {
  background-image: linear-gradient(red, yellow, green);
}
.layout {
  border: 1px solid #d7dde4;
  background: #f5f7f9;
  position: relative;
  border-radius: 4px;
  overflow: hidden;
}
.layout-logo {
  width: 100px;
  height: 30px;
  background: #5b6270;
  border-radius: 3px;
  float: left;
  position: relative;
  top: 15px;
  left: 20px;
}
.layout-nav {
  width: 420px;
  margin: 0 auto;
  margin-right: 20px;
}
</style>

<style scoped>
.layout {
  border: 1px solid #d7dde4;
  background: #f5f7f9;
  position: relative;
  border-radius: 4px;
  overflow: hidden;
}
.layout-header-bar {
  background: #fff;
  box-shadow: 0 1px 1px rgba(0, 0, 0, 0.1);
}
.layout-logo-left {
  width: 90%;
  height: 30px;
  background: #5b6270;
  border-radius: 3px;
  margin: 15px auto;
}
.menu-icon {
  transition: all 0.3s;
}
.rotate-icon {
  transform: rotate(-90deg);
}
.menu-item span {
  display: inline-block;
  overflow: hidden;
  width: 69px;
  text-overflow: ellipsis;
  white-space: nowrap;
  vertical-align: bottom;
  transition: width 0.2s ease 0.2s;
}
.menu-item i {
  transform: translateX(0px);
  transition: font-size 0.2s ease, transform 0.2s ease;
  vertical-align: middle;
  font-size: 16px;
}
.collapsed-menu span {
  width: 0px;
  transition: width 0.2s ease;
}
.collapsed-menu i {
  transform: translateX(5px);
  transition: font-size 0.2s ease 0.2s, transform 0.2s ease 0.2s;
  vertical-align: middle;
  font-size: 22px;
}
</style>
