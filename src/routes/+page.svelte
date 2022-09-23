<script>
	
	import Footer from './Footer.svelte'
	
	$: selection = "It's time to get'er done!"
	$: value = ''
	
	$: todos = []
	
	function create(){
		todos = [...todos, value]
		value = ''
		//console.log(todos)
		
	}

    function select() {
        console.log('click')
    }
	
</script>

<body>
	<h1>
		Todo List
	</h1>
	<div class="todo-list">
        <ol>
            {#each todos as task, i}
			    <li class="list-item"
                    on:click={select}>{task}</li>
		    {/each}
        </ol>

	</div>


	<section>
		<input type="text" 
					 placeholder="Enter a task..." 
					 bind:value/>
		<button on:click={create}>Create</button>
		<button on:click={() => selection = "read"}>Read</button>
		<button on:click={() => selection = "update"}>Update</button>
		<button on:click={() => selection = "delete"}>Delete</button>
	</section>
</body>

<Footer/>

<style>
	
    body{
        height:90vh;
        
    }
	h1 {
		
		text-align: center;
	}
	
	.todo-list{
		
		
		height: 150px;
		overflow-y: auto;
	}
	
	::-webkit-scrollbar {
    width: 12px;
}

	/* Track */
	::-webkit-scrollbar-track {
			-webkit-box-shadow: inset 0 0 6px rgba(0,0,0,0.3); 
			-webkit-border-radius: 10px;
			border-radius: 10px;
	}

	/* Handle */
	::-webkit-scrollbar-thumb {
			-webkit-border-radius: 10px;
			border-radius: 10px;
			background: rgba(255,0,0,0.8); 
			-webkit-box-shadow: inset 0 0 6px rgba(0,0,0,0.5); 
	}
	::-webkit-scrollbar-thumb:window-inactive {
			background: rgba(255,0,0,0.4); 
	}
	

    .list-item:hover{
        background-color: pink;
        font-weight: bolder;
    }
	section {
		
		display:flex;
        
        align-items:center;
		padding-top:25px;
		padding-bottom: 25px;
		flex-direction: column;
        background-color: blue;
	}
	
	input {
		

    
		border-radius: 5px;
		margin-bottom: 25px;
		height: 50px;
		font-size: 20px;
	}
	
	input:focus {
		
		filter: drop-shadow(0 0.2rem 0.25rem rgba(0, 0, 0, 0.3));
		outline: none;
	}

    button {
        height: 40px;
        width: 250px;
        
    }
	
</style>