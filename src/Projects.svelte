<script>
    import Kalman from "./Projects/Kalman.md"
	import Approximations from "./Projects/Approximations.md"
	import Monkey from "./Projects/Monkey.md"
	import PsychoSite from "./Projects/PsychoSite.md"
	let current = "monkey"
	function changeCurrent(newCurrent){
		current = newCurrent
	}
	let windowSize = window.innerWidth
	function newSize(){
		windowSize = window.innerWidth
		if (windowSize >600){
			dropdownOn = true
		}
	}
	let dropdownOn = false
</script>
<svelte:window on:resize={newSize}/>
<style>
    .selections{
    display:flex;
    flex-direction: row;
	top: 90px;
	position:relative;
	width: 600px;
	justify-content: space-evenly;
	left: calc(50vw - 310px)
    }
    .blog-container {
		left: 12vw; 
		position:relative; 
		width:70vw; 
		margin:20px;
		font-size: 1.5vw;
		z-index: 0;

	}
	.location{
		text-decoration-color: gold;
		background-color:#292b2c;
		color:#fff8e7;
		border:none;
		font-size:15px;
		border-radius:.5vw;
		width: auto;
	}
	button:active {
		border-style: outset;
		background-color:#292b2c;
		border:none
	}
	button:hover {
		cursor: pointer;
		text-decoration: underline
	}
	.blog-container > :last-child {
    margin-bottom: 3em;
}
	.project-drop {
		background-color:#292b2c;
		position:relative;
		width:175px;
		height:30px;
		left:-3px;
		top:0px;
		margin:0;
		color:#fff8e7;
		border:solid grey;
		text-decoration-color: gold;

	}
</style>
{#if windowSize > 600}
	<div class="selections" >
		<button on:click= {()=>changeCurrent("monkey")} class=location style = "{(current=="monkey")?"text-decoration:underline":""}">
			Monkey Brain Analysis
		</button>
		<button on:click= {()=>changeCurrent("kalman")} class=location style = "{(current=="kalman")?"text-decoration:underline":""}">
			Neural Kalman Filters
		</button>
		<button on:click= {()=>changeCurrent("approximations")} class=location style = "{(current=="approximations")?"text-decoration:underline":""}">
			Neuron Approximations
		</button>
		<button on:click= {()=>changeCurrent("psychosite")} class=location style = "{(current=="psychosite")?"text-decoration:underline":""}">
			PsychoSite
		</button>
	</div>
{:else}
	<div style="margin:0;width:200px;height:30px;top:90px;border-radius:10px;left:calc(50vw - 100px);background-color:#292b2c;position:relative">
		<div style="text-align:left;color:#fff8e7;top:-10px;position:relative;width:120px">
			<p style="left:30px;position:absolute">Select Project</p>
		</div>
		<button on:click={()=>{dropdownOn = !dropdownOn}} style="top:5px;left:150px;position:absolute;font-size:20px;height:10px;background-color:#292b2c">
			<h3 style="color:gold;top:-40px;position:relative">...</h3>
		</button>
		{#if dropdownOn}
			<div style = "text-align:right;color:#fff8e7;top:30px;position:absolute;z-index:1;">
					<button on:click= {()=>changeCurrent("monkey")} class = project-drop style = "{(current=="monkey")?"text-decoration:underline":""}">
						Monkey Brain Analysis
					</button>
					<button on:click= {()=>changeCurrent("kalman")} class = project-drop style="top:-3px;{(current=="kalman")?"text-decoration:underline":""}">
						Neural Kalman Filters
					</button>
					<button on:click= {()=>changeCurrent("approximations")} class = project-drop style="top:-6px;{(current=="approximations")?"text-decoration:underline":""}">
						Neuron Approximations
					</button>
					<button on:click= {()=>changeCurrent("psychosite")} class = project-drop style="left:-7px;top:-9px;{(current=="psychosite")?"text-decoration:underline":""}">
						PsychoSite
					</button>
			</div>
		{/if}
	</div>
{/if}

{#if current === "kalman"}
	<div class="blog-container kalman" style="top:100px">
		<div style="position:relative;border: .5vw solid #292b2c;border-radius: 1vw;padding:2vw">
			<Kalman></Kalman>
		</div>
	</div>
{/if}
{#if current === "monkey"}
<div class=blog-container style="top:100px">
	<div style="position:relative;border: .5vw solid #292b2c;border-radius: 1vw;padding:2vw">
		<Monkey></Monkey>
	</div>
</div>
{/if}
{#if current === "approximations"}
	<div class="blog-container approximations" style="top:100px">
		<div style="position:relative;border: .5vw solid #292b2c;border-radius: 1vw;padding:2vw">
			<Approximations></Approximations>
		</div>
	</div>
{/if}
{#if current === "psychosite"}
	<div class=blog-container style="top:100px">
		<div style="position:relative;border: .5vw solid #292b2c;border-radius: 1vw;padding:2vw">
			<PsychoSite></PsychoSite>
		</div>
	</div>
{/if}