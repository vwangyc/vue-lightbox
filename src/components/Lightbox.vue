<template>
	<div>
		<div class="wrapper" v-if="show">
			<span class="close" @click="closeImage">&times;</span>
			<img class="image" :src="showImage(`${filename}`)">	
		</div>
	</div>
</template>

<script>
import images from '@/images.js'

export default {
	name: "Lightbox",
	data () {
		return {
			images,
			show: false,
			filename: '',
		}
	},
	methods: {
		showImage(filename) {
			this.show = true;
			this.filename = filename
			return require('@/assets/images/' + filename)
		},
		closeImage() {
			this.show = false;
		},
	}
}
</script>

<style scoped>
.wrapper {
	align-items: center;
	background-color: rgba(0,0,0,.8);
	display: flex;
	height: 100%;
	justify-content: center;
	position: fixed;
	top: 0;
	width: 100%;
}
	
.close {
	color: white;
	cursor: pointer;
	font-size: 50px;
	padding: 10px 30px;
	position: absolute;
	right: 0;
	top: 0;	
}

.image {
	width: 60%;
}
</style>