<template>
	<div class="container">
		<input type="text" placeholder="请输入班课名称" v-model="courseName" class="input-box" />
		<input type="text" placeholder="请输入班级" v-model="courseClass" class="input-box" />
		<p>选择班课封面</p>
		<div class="preview" @click="handleClick()">
			<img :src="imgUrl" class="cover" v-if="!show" />
			<img src="../assets/plus.png" class="icon-plus" v-if="show" />
			<input type="file" @change="getFile($event)" style="display: none;" id="coverFile" />
		</div>
		<button @click="addCourse()" class="btn">确定</button>
	</div>
</template>

<script>
export default {
	name: 'NewCourse',
	data() {
		return {
			loginUserId: 1,
			courseName: '',
			courseClass: '',
			file: '',
			imgUrl: '',
			show: true
		};
	},
	methods: {
		//点击图片预览区，即模拟点击文件选择组件
		handleClick: function() {
			document.getElementById('coverFile').click();
		},
		//图片预览
		getFile: function() {
			this.file = event.target.files[0];
			var windowURL = window.URL || window.webkitURL;
			this.imgUrl = windowURL.createObjectURL(this.file);
			this.show = false;
		}
	
		
	}
};
</script>
<style scoped>
.container {
	display: flex;
	flex-direction: column;
	padding-top: 20px;
	padding-left: 100px;
	background-color: #fff;
	margin-top: 20px;
}
.input-box {
	width: 500px;
	height: 40px;
	margin-bottom: 40px;
	font-size: 14px;
}
.btn {
	margin-top: 20px;
	width: 120px;
	height: 40px;
	border: 2px solid rgb(0, 187, 221);
	background-color: #fff;
	border-radius: 8px;
	outline: none;
	color: rgb(0, 187, 221);
	font-size: 16px;
}
.preview {
	width: 150px;
	height: 150px;
	border: 2px dashed #aaa;
	cursor: pointer;
	display: flex;
	align-items: center;
	justify-content: center;
}
.icon-plus {
	width: 100px;
	height: 70px;
}
.cover {
	width: 100%;
	height: 100%;
}
</style>
