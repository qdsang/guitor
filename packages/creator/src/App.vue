<style lang="scss">
  .app {
    user-select: none;
  }
  .side-panel-navs {
    .el-tabs {
      .el-tabs__header  {
        margin-bottom: 0;
        .el-tabs__item {
          height: 50px;
          line-height: 50px;
          color: #fff;
        }
        .el-tabs__active-bar {
          height: 2px;
          background-color: orange;
        }
        .el-tabs__nav-wrap {
          margin-bottom: 0;
          &:after {
            display: none;
          }
        }
      }
    }
    .mu-tabs {
      background-color: transparent;
      .mu-tab {
        height: 50px
      }
    }
  }

  html {
    overflow-y: hidden !important;
  }
</style>
<template>
  <m-app id="app" class="app">
    <m-frame
      rightSize="500px"
      headerSize="50px"
      footerSize="60px"
      leftSize="260px"
      fillHeader="none"
      fillFooter="none"
      :leftIndex="5"
      :rightIndex="5">
      <m-flex width="100%" height="100%" align="center" justify="center">
        <previewer/>
      </m-flex>
      <timeline slot="footer" />
      <library slot="left" />
      <m-frame slot="right" class="side-panel" :header-size="50" :elevation="2">
        <m-app-bar slot="header" :size="50" class="side-panel-navs">
          <el-tabs v-model="activeName">
            <el-tab-pane label="API" name="comp-api"></el-tab-pane>
            <el-tab-pane label="样式" name="styles"></el-tab-pane>
            <el-tab-pane label="项目" name="project"></el-tab-pane>
            <el-tab-pane label="事件" name="flow"></el-tab-pane>
            <el-tab-pane label="帮助" name="FAQ"></el-tab-pane>
          </el-tabs>
        </m-app-bar>
        <keep-alive>
          <router-view></router-view>
        </keep-alive>
      </m-frame>
    </m-frame>
  </m-app>
</template>
<script>
  import Previewer from './components/previewer'
  import Timeline from './components/timeline'
  import ToolBar from './components/tool-bar'
  import Library from './components/library'

  export default {
    name: 'app',
    components: {
      Library,
      ToolBar,
      Previewer,
      Timeline
    },
    data () {
      return {
      }
    },
    computed: {
      activeName: {
        get () {
          return this.$route.name || 'comp-api'
        },
        set (name) {
          console.log(name)
          this.$router.push({
            name
          })
        }
      }
    },
    // methods: {
    //   isActive (name) {
    //     return this.$route.name === name
    //   },
    //   handleTo (name) {
    //     this.$router.push({
    //       name
    //     })
    //   }
    // },
    created () {

    },
    mounted () {
    }
  }
</script>
