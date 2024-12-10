<script setup>
// TODO: 编辑
import { ref } from 'vue'
// 弹框开关
const form = ref({name:'',place:'',id:''})
const dialogVisible = ref(false)
const open = (row) =>{
  dialogVisible.value = true
  form.value.name = row.name
  form.value.place = row.place
  form.value.id = row.id
}

defineExpose({
  open
})

const emit = defineEmits(['form-change'])

const editd = () =>{
emit('form-change',form.value)
dialogVisible.value = false

  
}

</script>

<template>
  <el-dialog v-model="dialogVisible" title="编辑" width="400px">
    <el-form label-width="50px">
      <el-form-item label="姓名">
        <el-input v-model="form.name" placeholder="请输入姓名" />
      </el-form-item>
      <el-form-item  label="籍贯">
        <el-input v-model="form.place" placeholder="请输入籍贯" />
      </el-form-item>
    </el-form>
    <template #footer>
      <span class="dialog-footer">
        <el-button @click="dialogVisible = false">取消</el-button>
        <el-button type="primary" @click="editd">确认</el-button>
      </span>
    </template>
  </el-dialog>
</template>

<style scoped>
.el-input {
  width: 290px;
}
</style>
