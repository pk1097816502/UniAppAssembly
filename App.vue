<script>
	export default {
		onLaunch: function() {
			console.log('App Launch');
			
			// #ifdef MP-WEIXIN
				this.getCode((res)=>{
					console.log("wx.login",res);
				});
			// #endif
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		},
		methods:{
			getCode(fun,provider=""){
				if(provider==""){
					uni.login({
						success:(res) => {
							console.log("uni.login",res);
							if(typeof fun == "function"){
								fun(res);
							}
						}
					})
				}else{
					uni.login({
						provider:provider,
						success:(res) => {
							if(typeof fun == "function"){
								fun(res);
							}
						}
					})
				}
			}
		}
	}
</script>

<style>
	/*每个页面公共css */
	@import url("//at.alicdn.com/t/font_1854820_ndamh6d6m9a.css");
	@import url("@/static/style/defalut.scss");
</style>
