<template>
  <div class="CopClass">
    <h1>{{ msg }}</h1>
    <h2>Element UI Button</h2>
    <el-button type="primary" @click="login">Show Channels</el-button>
    <el-table :data="channel_data" border justify="center" style="width: 100%">
      <el-table-column prop="title_chinese" label="ChannelName"></el-table-column>
      <el-table-column prop="short_description_chinese" label="Description"></el-table-column>
      <el-table-column prop="visible" label="Visible"></el-table-column>
    </el-table>
  </div>
</template>

<script>
    import Vue from 'vue'

    export default {
        name: 'CopName',
        data() {
            return {
                msg: 'Welcome to More DashBoard!',
                checked: true,
                channel_data:[]
            }
        },
        methods:{
            login:function () {

                var url='/api/managementfactor/selectAll'
                Vue.axios.get(url).then((response)=>{
                    this.channel_data = response.data;
                }).catch((error)=>{
                    console.log("error!"+error)
                })
            }
        }
    }
</script>


