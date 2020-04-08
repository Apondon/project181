<template>
  <div class="home">
      <el-row :gutter="20">
        <el-col :span="4">
          <div class="bkgw">
            <h4>全部书籍</h4>
            <div v-for="(item) in list" :key='item.id' class="bookmenu">
              <h5>{{item.title}}</h5>
              <p v-for="(items) in item.books" :key='items.id'>
                {{items.name}}
              </p>
            </div>
          </div>
        </el-col>
        <el-col :span="20">
          <div class="banner"></div>
          <!-- 卡片 -->
          <el-row :gutter="10">
            <el-col :span="12" v-for="(item) in cards" :key="item.id">
              <el-card>
                <el-row :gutter="0">
                  <el-col :span="8">
                    <img src="https://shadow.elemecdn.com/app/element/hamburger.9cf7b091-55e9-11e9-a976-7f4d0b07eef6.png" height="100%" class="image">
                  </el-col>
                  <el-col :span="16">
                    <span class="card_title">{{item.title}}</span>
                    <p class="mtp10">{{item.text}}</p>
                    <p>{{item.text}}</p>
                    <el-button type="primary" class="buyBtn" @click="clickHandle">立即购买</el-button>
                  </el-col>
                </el-row>
              </el-card>
            </el-col>
          </el-row>
          <!-- 卡片结束 -->
        </el-col>
      </el-row>
  </div>
</template>

<script>

export default {
  data(){
    return{
      list:[
        {
          id:1,
          title:'移动互联网开发专业书籍',
          books:[
            {
              id:'pro1',
              name:'web标准网页设计之道'
            },
            {
              id:'pro2',
              name:'photoshop商业网站设计'
            },
            {
              id:'pro3',
              name:'c#编程基础'
            },
            {
              id:'pro4',
              name:'sql server数据库基础'
            },
            {
              id:'pro5',
              name:'java语言基础'
            },
            {
              id:'pro6',
              name:'java面向对象编程'
            },
            {
              id:'pro7',
              name:'java语言高级特性'
            },
          ]
        },
        {
          id:2,
          title:'移动互联网应用专业书籍',
          books:[
            {
              id:'apl1',
              name:'计算机基础应用'
            },
            {
              id:'apl2',
              name:'linux系统管理'
            },
            {
              id:'apl3',
              name:'企业网络互联技术'
            },
            {
              id:'apl4',
              name:'windows网络服务管理'
            },
            {
              id:'apl5',
              name:'windows系统管理'
            },
            {
              id:'apl6',
              name:'windows活动目录管理'
            },
            {
              id:'apl7',
              name:'计算机网络技术'
            },
          ]
        }
      ],
      cards:[
        {
          id:1,
          img:'',
          title:'移动互联网开发全套书籍',
          text:'移动互联网开发配套的书籍有好几本然后买不买无所谓就是凑数的'
        },
        {
          id:2,
          img:'',
          title:'移动互联网应用全套书籍',
          text:'移动互联网开发配套的书籍有好几本然后买不买无所谓就是凑数的'
        },
        {
          id:3,
          img:'',
          title:'大数据全套书籍',
          text:'移动互联网开发配套的书籍有好几本然后买不买无所谓就是凑数的'
        },
        {
          id:4,
          img:'',
          title:'人工智能全套书籍',
          text:'移动互联网开发配套的书籍有好几本然后买不买无所谓就是凑数的'
        },
      ]
    }
  },
  methods:{
    clickHandle(){
      this.$router.push('/detail')
    }
  }
}
</script>
<style lang="scss" scoped>
.home{
  // padding: 20px 0;
  h4,h5,p{
    margin: 0;
    text-indent: 10px;
  }
  h4{
    height: 40px;
    line-height: 40px;
    background: navy;
    color: #fff;
  }
  h5{
    height: 55px;
    line-height: 55px;
    font-weight: 100;
    font-size: 20px;
  }
  p{
    height: 30px;
    line-height: 30px;
  }
  .bookmenu{
    margin-bottom: 3px;
    background: #fff;
  }
  
  .banner{
    height:300px;
    background: navy;
    margin-bottom: 20px;
  }
  .card_title{
    padding-left: 10px;;
    font-size: 22px;
    font-weight: 600;
  }
  .mtp10{
    margin-top: 10px;
  }
  .buyBtn{
    margin: 20px 0 0 10px;
  }
}
</style>
