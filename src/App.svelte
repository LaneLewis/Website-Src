<script id="MathJax-script">
	import { fade } from 'svelte/transition';
	import Logo from "./Logo.svelte"
	import Projects from "./Projects.svelte"
	import Home from "./Home.svelte"
	function toGithub(){
		window.location.href ="https://github.com/LaneLewis" 
	}
	function toLinkedin(){
		window.location.href = "https://www.linkedin.com/in/lane-lewis-b7058b20a/"
	}
	function switchCurrent(loc){
		current = loc
	}
	let current = "home"
	let windowSize = window.innerWidth
	function newSize(){
		windowSize = window.innerWidth
		if (windowSize < 600){
			expandNav = false
		}
	}
	let expandNav = false
</script>

<style>
	body{
	background-color: #fff8e7;
    font-family: Garamond, serif;
    box-shadow: inset 0px 0px 20px 5px #292b2c;
	box-sizing: border-box;
	position:fixed;
	overflow-y: scroll;
	overflow-x: hidden;
	left:0;
	top:0;
	scroll-padding-bottom: 100px;
	margin:0;
}

.navbar{
	left: 0;
	top: 0;
	position: absolute;
	width: 100vw;
	height: 75px;
	background-color: #292b2c;
}
button:hover{
	cursor:pointer;
}
.location{
	text-decoration-color: gold;
	background-color:#292b2c;
	border:none;
	color:#fff8e7;
	font-size:22px
}
.location:hover{
	text-decoration: underline;
}
button:active {
	background-color:#292b2c;
}
.dropdown {
	margin:0;
	top:0px;
	width:100vw;
	height:50px;
	background-color:#292b2c;
	text-align:center;
	position:relative;
	border: solid grey;
	color:#fff8e7;
	text-decoration-color: gold;
}
</style>
<svelte:window on:resize={newSize}/>
<body>
	{#if windowSize > 600}
		{console.log(window.innerWidth)}
		<div class = navbar style="top:0;left:0">
			<div style = "top:3px; position: absolute; left:calc(100vw - 200px); display:flexbox; width:200px">
				<button on:click = {toGithub} style="background-color:#292b2c;border:none;width:60px;height:60px">
					<svg xmlns="http://www.w3.org/2000/svg" width="50" height="50" fill=#fff8e7 viewBox="0 0 24 24"><path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg>
				</button>
				<button on:click = {toLinkedin} style="background-color:#292b2c;border:none;width:60px;height:60px">
					<svg xmlns="http://www.w3.org/2000/svg" width="50" height="50" fill=#fff8e7 viewBox="0 0 24 24"><path d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-3.368-4-3.113-4 0v5.604h-3v-11h3v1.765c1.396-2.586 7-2.777 7 2.476v6.759z"/></svg>
				</button>
			</div>
			<div style="left:calc(50vw - 45px); position:absolute; top:0">
				<Logo/>
			</div>
			<div style="display:flexbox;flex-direction:row;top:18px;position:absolute;left:50px">
				<button class="location" on:click={()=>{switchCurrent("home")}} style="{(current=="home")?"text-decoration:underline":""}">
					Home
				</button>
				<button class="location" on:click = {()=>{switchCurrent("projects")}} style="{(current=="projects")?"text-decoration:underline":""}">
					Projects
				</button>
			</div>
		</div>
	{:else}
		<div class = navbar style="position:absolute;top:0;left:0;" >
			<div style = "top:3px; position: absolute; left:20px; display:flexbox; width:200px">
				<button on:click = {toGithub} style="background-color:#292b2c;border:none;width:60px;height:60px">
					<svg xmlns="http://www.w3.org/2000/svg" width="50" height="50" fill=#fff8e7 viewBox="0 0 24 24"><path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg>
				</button>
				<button on:click = {toLinkedin} style="background-color:#292b2c;border:none;width:60px;height:60px">
					<svg xmlns="http://www.w3.org/2000/svg" width="50" height="50" fill=#fff8e7 viewBox="0 0 24 24"><path d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-3.368-4-3.113-4 0v5.604h-3v-11h3v1.765c1.396-2.586 7-2.777 7 2.476v6.759z"/></svg>
				</button>
			</div>
			<button  on:click = {()=>{expandNav = !expandNav}} style="width:55px;height:55px;top:10px;border:solid #fff8e7;position:relative;left:calc(100vw - 90px);border-radius:8px;background-color:#292b2c">
				<div style="left:-1px;top:-5px;width:40px;height:3px;background-color:#fff8e7;position:relative;border-radius:2px"></div>
				<div style="left:-1px;top:0px;width:40px;height:3px;background-color:#fff8e7;position:relative;border-radius:2px"></div>
				<div style="left:-1px;top:5px;width:40px;height:3px;background-color:#fff8e7;position:relative;border-radius:2px"></div>
			</button>
		</div>
			{#if expandNav}
				<div style="position:relative;top:65px;left:-8px;" in:fade out:fade>
					<button class= dropdown on:click = {()=>switchCurrent("home")} style="{(current=="home")?"text-decoration:underline":""}">
						Home
					</button>
					<button class= dropdown on:click = {()=>switchCurrent("projects")} style=" top:-3px;{(current=="projects")?"text-decoration:underline":""}">
						Projects
					</button>
				</div>
			{/if}
	{/if}
	{#if current === "home"}
		<Home/>
	{/if}
	{#if current === "projects"}
		<Projects/>
	{/if}
</body>
