<template>
	<view class="page">
        <button type="primary" @click="choosePhoto">选择图片</button>
		<image :src="tailorPath" v-if="tailorPath"></image>
		<picture-tailor ref="pictureTailor" :pictureSrc="photoSrc" @createImg="createImg"></picture-tailor>
	</view>
</template>

<script>
	import pictureTailor from "../../components/picture-tailor/pictureTailor.vue";
	
	export default {
		data() {
			return {
				photoSrc: "",
				tailorPath: ""
			}
		},
		methods: {
			choosePhoto() {
				uni.chooseImage({
					count: 1,
					sizeType: ["compressed"],
					success: (res) => {
						this.photoSrc = res.tempFilePaths[0];
						this.$refs.pictureTailor.onShow();
					}
				});
			},
			createImg(e) {
				this.tailorPath = e;
			}
		},
		onBackPress() {
			if (this.$refs.pictureTailor.isShow) {
				this.$refs.pictureTailor.onHide();
			}
			return true;
		},
		onLoad() {

		},
		components: {
			pictureTailor
		}
	}
</script>

<style scoped>
	button {
		width: 80%;
	}
	
	image {
		width: 240upx !important;
		height: 240upx !important;
		margin: 80upx auto 0;
	}
</style>
