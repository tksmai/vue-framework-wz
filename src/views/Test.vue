<template>
	<div class="animated fadeIn">
		<Row>
			<Col :sm="24" :md="24" :lg="12">
				<h3>这是一个测试标题 </h3>
				<p>这是一个测试段落</p>
				<Table :columns="columns1" :data="data1"></Table>
			</Col>
		</Row>
		
	</div>
</template>

<style scoped>

</style>

<script>
export default {
	data() {
		return {
			columns1: [
				{
					title: "姓名",
					key: "name"
				},
				{
					title: "年龄",
					key: "age"
				},
				{
					title: "地址",
					key: "address"
				},
				{
					title: "操作",
					key: "action",
					width: 150,
					align: "center",
					render: (h, params) => {
						return h("div", [
							h("Button", {
								props: {
									type: "primary",
									size: "small"
								},
								style: {
									marginRight: "5px"
								},
								on: {
									click: () => {
										console.group()
										console.log("Click This Show Button!")
										console.log(params.index)
										console.log(params)
										console.groupEnd()
										this.show(params.index)
									}
								}
							}, '查看'),
							h('Button', {
								props: {
									type: 'error',
									size: 'small'
								},
								on: {
									click: () => {
										console.group()
										console.log("Click This Remove Button!")
										console.log(params.index)
										console.log(params)
										console.groupEnd()
										this.remove(params.index)
									}
								}
							}, '删除')
						])
					}
				}
			],
			data1: [
				{
					name: "王晓明",
					age: 14,
					address: "顺德汽车客运总站"
				},
				{
					name: "李晓虹",
					age: 28,
					address: "容桂客运站"
				},
				{
					name: "王明",
					age: 14,
					address: "顺德汽车客运总站"
				},
				{
					name: "王晓",
					age: 14,
					address: "顺德汽车客运总站"
				}
			],
		}
	},
	methods: {
		show (index) {
			this.$Modal.success({
				title: '用户信息 这是测试的用户信息',
				content: `姓名：${this.data1[index].name}<br />年龄：${this.data1[index].age}<br />地址：${this.data1[index].address}`
			})
		},
		remove (index) {
			this.data1.splice(index, 1)
		}
	}
}
</script>
