<template>
    <div>
        <el-row :gutter="20">
            <el-col :span="6">
                <div class="el-icon-pie-chart"></div>
                <div class="bookList">
                    <p v-for='item in list' :key='item.id' :class="item.class">
                        {{item.name}}
                    </p>
                </div>
                
            </el-col>
            <el-col :span="18">
                <!-- 上 -->
                <div class="upPart">
                    <h1>{{name}}</h1>
                    <p class="text">{{text}}</p>
                    <el-form ref="form" :model="form" label-width="80px">
                        <el-form-item label="书籍名称">
                            <el-radio-group v-model="form.name" @change="redioChangeHandle">
                                <el-radio-button v-for="item in bookList" :key="item.id" :label="item.name" ></el-radio-button>
                            </el-radio-group>
                        </el-form-item>
                        <el-form-item label="购买数量">
                            <el-input-number v-model="form.count" :min="1"></el-input-number>
                        </el-form-item>
                        <el-form-item label="适用校区">
                            <el-select v-model="form.school" placeholder="请选择">
                                <el-option
                                v-for="item in schools"
                                :key="item.value"
                                :label="item.label"
                                :value="item.value">
                                </el-option>
                            </el-select>
                        </el-form-item>
                        <el-form-item label="总价">
                            {{price}}
                        </el-form-item>
                    </el-form>
                    <el-button type="primary" class="buyButton">立即购买</el-button>
                </div>
                <!-- 下 -->
                <div class="downPart">
                    <h1>书籍简介</h1>
                    <p>{{content}}</p>
                </div>
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
                    name:'移动互联网开发书籍',
                    text:'这是移动互联网开发书籍里面的text',
                    books:[
                        {
                            id:'a1',
                            name:'C#语言基础',
                            price:30,
                            text:'碰碰运气”是老百姓们常说的一句话，是指一个人或者几个人在将要做什么事情的时候，对于无法预料的事情的一种心理安慰，也算是一种心理暗示，有赌的一层面意思。'
                            
                        },
                        {
                            id:'a2',
                            name:'java语言基础',
                            price:35,
                            text:'碰碰运气是安慰自己积极向上的心态'
                        },
                        {
                            id:'a3',
                            name:'C#高级应用',
                            price:40,
                            text:'...'
                        }
                    ],
                    class:''
                },
                {
                    id:2,
                    name:'移动互联网应用书籍',
                    text:'这是移动互联网应用书籍里面的text',
                    books:[
                        {
                            id:'b1',
                            name:'javascript语言基础',
                            price:30,
                            text:'asdasdadssadad'
                        },
                        {
                            id:'b2',
                            name:'html语言基础',
                            price:35,
                            text:'sdfghjklfghjklasdfghjkl;asxcvbnm'
                        },
                        {
                            id:'b3',
                            name:'javascript高级应用',
                            price:40,
                            text:'asdzxcvbnm,asdfghjkl;qwertyuiop[234567890-=zxcvbnm,./asdrftyu'
                        }
                    ],
                    class:''
                },
                {
                    id:3,
                    name:'大数据书籍',
                    text:'这是大数据书籍里面的text',
                    books:[
                        {
                            id:'c1',
                            name:'C#语言基础',
                            price:30
                        },
                        {
                            id:'c2',
                            name:'C#语言基础',
                            price:30
                        },
                        {
                            id:'c3',
                            name:'C#语言基础',
                            price:30
                        }
                    ],
                    class:''
                },
                {
                    id:4,
                    name:'人工智能书籍',
                    text:'这是人工智能书籍里面的text',
                    books:[
                        {
                            id:'d1',
                            name:'C#语言基础',
                            price:30
                        },
                        {
                            id:'d2',
                            name:'C#语言基础',
                            price:30
                        },
                        {
                            id:'d3',
                            name:'C#语言基础',
                            price:30
                        }
                    ],
                    class:''
                },
            ],
            schools: [{
                value: '选项1',
                label: '南阳校区'
                }, {
                value: '选项2',
                label: '郑州校区'
                }, {
                value: '选项3',
                label: '麻省理工'
                }, {
                value: '选项4',
                label: '哈佛大学'
                }, {
                value: '选项5',
                label: 'UCLA'
            }],
            form:{
                name:'',
                count:1,
                school:'',
                price:0,
            },
            bookList:[],
            id:0,
            name:'',//书名
            text:'',//简介
            content:'', //书籍内容简介
        }
    },
    mounted(){
        const id = this.$route.query.id
        this.list.map((item)=>{
            if(item.id == id){
                item.class='active' 
                this.bookList = item.books
                this.name = item.name
                this.text = item.text
            } 
        })
    },
    computed:{
        price(){
            return this.form.price*this.form.count
        }
    },
    methods:{
        redioChangeHandle(){
            console.log()
            this.bookList.map((item)=>{
            if(item.name == this.form.name) {
                this.form.price = item.price
                this.content = item.text
            }
        })
        }
    }
}
</script>
<style lang="scss" scoped>
div.el-icon-pie-chart{
    height: 150px;
    line-height: 150px;
    width:100%;
    font-size: 60px;
    color: orange;
    font-weight: 900;
    text-align: center;
}
.bookList{
    p{
        height: 30px;
        line-height: 30px;
    }
}
.active{
    background: cyan;
    color: #fff;
}
.text{
    height: 40px;
    line-height: 40px;
    background: rgb(253, 255, 142);
    color: grey;
    font-size: 14px;
    text-indent: 20px;
}
.el-radio-button{
    margin-right:15px ;
}
.buyButton{
    margin-left: 40px;
}
</style>