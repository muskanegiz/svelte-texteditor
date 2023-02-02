<script>
// @ts-nocheck

	import Icon from 'svelte-awesome';
	import link from 'svelte-awesome/icons/link';
	import listOl from 'svelte-awesome/icons/listOl';
	import listUl from 'svelte-awesome/icons/listUl';
	import { onMount } from 'svelte';
	function links() {
		var url = window.prompt('Enter the link URL');
		if (url) exec('createLink', url);
	}

    var selection = ``;
    onMount(() => {
        // Once the component is mounted, we can access the document:
        document.addEventListener(`selectionchange`, () => {
            selection = document.getSelection();
        });
		
    });
	

	function unlist(){
	// @ts-ignore
	let selection = window.getSelection();
	var name= document.getElementById("myElement").innerHTML;
	var count = name?.replaceAll("\n", ",")
	console.log(count);
	// @ts-ignore
	const myArray = count.split(",");
	console.log(myArray);
		var tx= "";
		for(var i=0; i<myArray.length;i++){
			tx+= "<li>"+myArray[i]+"</li>";
		}
		// @ts-ignore
		document.getElementById("ulist").innerHTML=tx;
		console.log("hello");
  		selection.deleteFromDocument();
		console.log(tx);
	}


	
</script>


<nav class="bg-gray-800 w-1/2 mx-auto mt-10">
	<div class="mx-auto max-w-7xl px-2 sm:px-6 lg:px-8">
	  	<div class="relative flex h-16 items-center justify-between">
			<div class="absolute inset-y-0 left-0 flex items-center sm:hidden">
				<button type="button" class="inline-flex items-center justify-center rounded-md p-2 text-gray-400 hover:bg-gray-700 hover:text-white focus:outline-none focus:ring-2 focus:ring-inset focus:ring-white" aria-controls="mobile-menu" aria-expanded="false">
					<span class="sr-only">Open main menu</span>
					<svg class="block h-6 w-6" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" aria-hidden="true">
					<path stroke-linecap="round" stroke-linejoin="round" d="M3.75 6.75h16.5M3.75 12h16.5m-16.5 5.25h16.5" />
					</svg>
					<svg class="hidden h-6 w-6" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" aria-hidden="true">
					<path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
					</svg>
				</button>
			</div>
			<div class="flex flex-1 items-center justify-center sm:items-stretch sm:justify-start">
				<div class="flex flex-shrink-0 items-center">
					<img class="block h-8 w-auto lg:hidden" src="https://tailwindui.com/img/logos/mark.svg?color=indigo&shade=500" alt="Your Company">
					<img class="hidden h-8 w-auto lg:block" src="https://tailwindui.com/img/logos/mark.svg?color=indigo&shade=500" alt="Your Company">
				</div>
				<div class="hidden sm:ml-6 sm:block">	 
					<div class="flex space-x-4">
						<button class="fontStyle bg-gray-900 text-white px-3 py-2 rounded-md text-sm font-medium" 
						on:click={()=>{document.execCommand( 'bold',false)}} title="Bold Highlighted Text"><b>B</b>
						</button>
						<button class="fontStyle bg-gray-900 text-white px-3 py-2 rounded-md text-sm font-medium italic" 
						on:click="{()=>{document.execCommand('italic',false)}}" title="Italicize Highlighted Text"><i>I</i>
						</button>  
						<button class="fontStyle bg-gray-900 text-white px-3 py-2 rounded-md text-sm font-medium underline underline-offset-4" 
						on:click={()=>{document.execCommand( 'underline',false)}} title='Underline Highlighted Text'><u>U</u>
						</button>
						<a href={"#"} class="bg-gray-900 text-white px-3 py-2 rounded-md text-sm font-medium" aria-current="page"
						on:click={links}> 
						<Icon data={link}/></a>
						<a href={"#"} class="bg-gray-900 text-white px-3 py-2 rounded-md text-sm font-medium" aria-current="page"
						on:click={()=>{document.execCommand('insertOrderedList')}}>
						<Icon data={listOl}/></a>
					</div>
				</div>
			</div>
	  	</div>
	</div>  
</nav>

<div class="flex justify-center">
	<div class="mb-3 w-1/2">
	  	<label for="exampleFormControlTextarea1" class="form-label inline-block mb-2 text-gray-700"></label>
	  	<fieldset id="editor" contenteditable="true"
		class="h-64
		block
		w-full
		px-3
		py-3
		text-base
		font-normal
		text-gray-700
		bg-white bg-clip-padding
		border border-solid border-gray-300
		rounded
		transition
		ease-in-out
		m-0
		focus:text-gray-700 focus:bg-white focus:border-blue-600 focus:outline-none
		" >	
		<ol id="olist" class="list-decimal list-index m-2" type="1"></ol>
		<ul id="ulist" class="list-disc list-index m-2" ></ul>
		</fieldset>
	</div>
</div>


<p id="myElement" class="hidden"> {selection}</p>



