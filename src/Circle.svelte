<script>    
    export let emoji = ['📄', '🤝', '🤫', '👋', '❌', '😘', '🚘', '💪']
	export let arr = ['page', 'handshake', 'shush', 'greeting', 'cross', 'kiss', 'car', 'biceps'];

    export let centerImg = '👋';

	export let itemValue = 'greeting';

	$: centerValue = itemValue;

	export const setCenterImg = (value) => {
		let idx = arr.findIndex(item => item === value);
		return emoji[idx];
	}

	export const clickHandler = (e) => {
		console.log(e.target.value);
		itemValue = e.target.value;
		centerImg = setCenterImg(itemValue);
	}
</script>


<nav>
    <div class="settings">Settings-Block</div>			
    <ul class="circle-menu">
        <li class="page slice">
            <!-- svelte-ignore a11y-mouse-events-have-key-events -->
            <button class="circle-menu" value={arr[0]} on:mouseover={(e)=>clickHandler(e)}>{emoji[0]}</button>
        </li>
        <li class="handshake slice">
            <!-- svelte-ignore a11y-mouse-events-have-key-events -->
            <button class="circle-menu" value={arr[1]} on:mouseover={(e)=>clickHandler(e)}>{emoji[1]}</button>
        </li>
        <li class="shush slice">
            <button class="circle-menu" value={arr[2]} on:click={(e)=>clickHandler(e)}>{emoji[2]}</button>
        </li>
        <li class="greeting slice">
            <button class="circle-menu" value={arr[3]} on:click={(e)=>clickHandler(e)}>{emoji[3]}</button>
        </li>
        <li class="cross slice">
            <button class="circle-menu" value={arr[4]} on:click={(e)=>clickHandler(e)}>{emoji[4]}</button>
        </li>
        <li class="kiss  slice">
            <button class="circle-menu" value={arr[5]} on:click={(e)=>clickHandler(e)}>{emoji[5]}</button>
        </li>
        <li class="car slice">
            <button class="circle-menu" value={arr[6]} on:click={(e)=>clickHandler(e)}>{emoji[6]}</button>
        </li>
        <li class="biceps slice">
            <div>
                <b>{emoji[7]}</b>
                <button class="circle-menu" value={arr[7]} on:click={(e)=>clickHandler(e)} >{emoji[7]}</button>
            </div>								
        </li>
        <li class="center circle-menu">				
            <button on:click={()=> console.log('test1')}>{centerImg}</button>				
        </li>
    </ul>		
</nav>
