<template>
    <ul>
        <li v-for = "(item,index) in list" :key="index">
            {{item}}
        </li>
    </ul>
</template>

<script>
export default {
    name: "Login",
    data() {
        return {
            list:['我的任务','通知管理','项目立项','项目管理']
        }
    }
}
</script>

<style>

</style>