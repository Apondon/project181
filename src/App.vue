<template>
  <div id="app">
    <el-container>
      <el-header class='hdr'>
        <el-row :gutter="20">
          <el-col :span="8"><div class="logo">小莱书城</div></el-col>
          <el-col :span="16">
            <div class="breadcrumb">
              <el-breadcrumb separator="|">
                <el-breadcrumb-item><span @click="loginVisible = true">登录</span></el-breadcrumb-item>
                <el-breadcrumb-item><span @click="registVisible = true">注册</span></el-breadcrumb-item>
                <el-breadcrumb-item><span @click="aboutVisible = true">关于</span></el-breadcrumb-item>
              </el-breadcrumb>
            </div>
          </el-col>
        </el-row>
      </el-header>
      <el-main class="ctt">
        <div class="inner">
          <router-view/>
        </div>
      </el-main>
      <el-footer class="ftr">Footer</el-footer>
    </el-container>
    <!-- 登录 -->
    <el-dialog :visible.sync="loginVisible">
      <el-form :model="loginForm">
        <el-form-item label="账号" :label-width="formLabelWidth">
          <el-input v-model="loginForm.account" autocomplete="off"></el-input>
        </el-form-item>
        <el-form-item label="密码" :label-width="formLabelWidth">
          <el-input v-model="loginForm.password" autocomplete="off"></el-input>
        </el-form-item>
      </el-form>
      <div slot="footer" class="dialog-footer">
        
        <el-button type="primary" @click="loginVisible = false">登 录</el-button>
      </div>
    </el-dialog>
    <!-- 注册 -->
    <el-dialog :visible.sync="registVisible">
      <el-form :model="registForm">
        <el-form-item label="账号" :label-width="formLabelWidth">
          <el-input v-model="registForm.account" autocomplete="off"></el-input>
        </el-form-item>
        <el-form-item label="密码" :label-width="formLabelWidth">
          <el-input v-model="registForm.password" autocomplete="off"></el-input>
        </el-form-item>
        <el-form-item label="确认密码" :label-width="formLabelWidth">
          <el-input v-model="registForm.cfmpassword" autocomplete="off"></el-input>
        </el-form-item>
      </el-form>
      <div slot="footer" class="dialog-footer">
        <el-button type="primary" @click="registVisible = false">提 交</el-button>
      </div>
    </el-dialog>
    <!-- 关于 -->
    <el-dialog :visible.sync="aboutVisible" >
      <span>需要设置visible属性，它接收Boolean，当为true时显示 Dialog。Dialog 分为两个部分：body和footer，footer需要具名为footer的slot。title属性用于定义标题，它是可选的，默认值为空。</span>
    </el-dialog>
    
  </div>
</template>
<script>
export default {
  data(){
    return{
      // 登录
      loginVisible:false,
      loginForm:{
        account:'',
        password:''
      },
      // 注册
      registVisible : false,
      registForm:{
        account:'',
        password:'',
        cfmpassword:''
      },
      // 关于
      aboutVisible:false,
      // label的宽度
      formLabelWidth: '120px'
    }
  }
}
</script>
<style lang="scss">
*{
  margin:0;
  padding:0;
}
html,body{
  height: 100%;
  margin: 0;
  padding: 0;
}
#app{
  height: 100%;
  section{
    height: 100%;
  }
  .hdr{
    background: navy;
    .logo{
      line-height: 60px;
      color: #fff;
      font-size: 40px;
    }
    .breadcrumb{
      height: 60px;
      .el-breadcrumb{
        line-height: 60px;
        box-sizing: border-box;
        padding-left: 70%;
        span{
          color:#fff;
        }
      }
    }
  }
  .ctt{
    background: #f4f4f4;
  }
  .ftr{
    background: gainsboro;
  }
}
</style>
