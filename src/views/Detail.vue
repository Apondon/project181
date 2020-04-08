<template>
    <div>
        <el-row :gutter="20">
            <el-col :span="6">
                <div class=".el-icon-pie-chart"></div>
                <p v-for='item in list' :key='item.id'>
                    {{item.name}}
                </p>
            </el-col>
            <el-col :span="18">
                <!-- 上 -->
                <div class="upPart">
                    <h1>{{name}}</h1>
                    <p>{{text}}</p>
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
                },
                {
                    id:2,
                    name:'移动互联网应用书籍',
                },
                {
                    id:3,
                    name:'大数据书籍',
                },
                {
                    id:4,
                    name:'人工智能书籍',
                },
            ],


            name:'',//书名
            text:'',//简介
            content:'', //书籍内容简介
        }
    }
}
</script>
<style lang="scss" scoped>

</style>