<script>
	import TweetForm from './TweetForm.svelte';
</script>

<style>
	.title{
		color:#f6fcff;
		font-size:36px;
		font-weight:600;
	}
	.sub-title{
		color:#f3f6f9;
		font-weight:600;
		text-decoration: underline;
	}
	.main{
		height: 100%;
		padding:50px;
		background:hsl(157, 30%, 46%);
	}
</style>

<div class="main">
	<div class="title">Click to tweet generator</div>
	<TweetForm/>
	<a class="sub-title"
	   href='https://xq-is-here.medium.com/'
	   target="_blank"
	   rel="noopener noreferrer">Made with <span style="color: #e25555;">&#9829;</span> Kunal
	</a>
</div>
