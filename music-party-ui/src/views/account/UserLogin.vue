<template>
    <div class="main">
        <DocBlock :type="'info'" title="登录" icon="fa-solid:user" context="这是一个登录页面" />
        <el-divider content-position="left">登录页</el-divider>
        <div class="edit_area">
            <el-form :model="userInfo" label-width="auto" style="max-width: 600px">
                <el-form-item label="用户名">
                    <el-input v-model="userInfo.name" />
                </el-form-item>
                <el-form-item label="密码">
                    <el-input v-model="userInfo.password" />
                </el-form-item>
                <el-form-item label="">
                    <el-button type="primary" @click="userLogin">登录</el-button>
                </el-form-item>
            </el-form>
        </div>
    </div>
</template>

<script setup lang="ts">
import { reactive } from 'vue';
import { type UserInfoInter } from '@/types/account';
import DocBlock from '@/components/DocBlock.vue';
import { useUserStore } from '@/store/userStore';

const store = useUserStore();

const userInfo: UserInfoInter = reactive({
    id: 0,
    name: "",
    password: "",
    bind: {
        netease: 0,
        bilibili: 0
    },
    role: []
})

const userLogin = () => {
    store.login(userInfo.name.toString(), userInfo.password.toString())
}

</script>

<style scoped>
.main {
    margin: 2rem;
}
</style>