<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style>
	/*每个页面公共css */
	page,
	view {
		display: flex;
	}

	page {
		background-color: #f5f5f5;
		min-height: 100%;
	}

	.page {
		display: flex;
		flex: 1;
		flex-direction: column;
		width: 100%;
	}
</style>
