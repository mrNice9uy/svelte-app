<script>
    import {arr, emoji, arrRus} from './constants/constans'
    
    export let centerImg = '👋';

	export let itemValue = 'greeting';

    export let actionTitle = 'Поздороваться';

	export const setCenterImg = (value) => {
		let idx = arr.findIndex(item => item === value);
		return emoji[idx];
	}

    export const setActionTitle = (value) => {
        let idx = arr.findIndex(item => item === value);
        return arrRus[idx];
    }

    export const showActionValue = (e, value) => {
        let btn = document.querySelector('.center-btn__btn')
        btn.addEventListener('contextmenu', event => event.preventDefault());
        if (e.which === 1) {
            console.log('use action',value);                        
        } else if (e.which ==3) {
            console.log('delete action',value)
            return false
        }
    }

	export const mouseHandler = (e) => {
		itemValue = e.target.value;
		centerImg = setCenterImg(itemValue);
        actionTitle = setActionTitle(itemValue)
	}
</script>


<nav>
    <div class="settings" on:click={()=>console.log('settings')}><h2>⚙️</h2></div>			
    <ul class="circle-menu">
        <li class="page slice">
            <!-- svelte-ignore a11y-mouse-events-have-key-events -->
            <button class="circle-menu" value={arr[0]} on:mouseover={(e)=>mouseHandler(e)}>{emoji[0]}</button>
        </li>
        <li class="handshake slice">
            <!-- svelte-ignore a11y-mouse-events-have-key-events -->
            <button class="circle-menu" value={arr[1]} on:mouseover={(e)=>mouseHandler(e)}>{emoji[1]}</button>
        </li>
        <li class="shush slice">
            <!-- svelte-ignore a11y-mouse-events-have-key-events -->
            <button class="circle-menu" value={arr[2]} on:mouseover={(e)=>mouseHandler(e)}>{emoji[2]}</button>
        </li>
        <li class="greeting slice">
            <!-- svelte-ignore a11y-mouse-events-have-key-events -->
            <button class="circle-menu" value={arr[3]} on:mouseover={(e)=>mouseHandler(e)}>{emoji[3]}</button>
        </li>
        <li class="cross slice">
            <!-- svelte-ignore a11y-mouse-events-have-key-events -->
            <button class="circle-menu" value={arr[4]} on:mouseover={(e)=>mouseHandler(e)}>{emoji[4]}</button>
        </li>
        <li class="kiss slice">
            <!-- svelte-ignore a11y-mouse-events-have-key-events -->
            <button class="circle-menu" value={arr[5]} on:mouseover={(e)=>mouseHandler(e)}>{emoji[5]}</button>
        </li>
        <li class="car slice">
            <!-- svelte-ignore a11y-mouse-events-have-key-events -->
            <button class="circle-menu" value={arr[6]} on:mouseover={(e)=>mouseHandler(e)}>{emoji[6]}</button>
        </li>
        <li class="biceps slice">
            <!-- svelte-ignore a11y-mouse-events-have-key-events -->
            <button class="circle-menu" value={arr[7]} on:mouseover={(e)=>mouseHandler(e)} >{emoji[7]}</button>        
        </li>
        <li class="center circle-menu">	
            <div class="center-btn">
                <button class="center-btn__btn" on:mousedown={(e)=> showActionValue(e, itemValue)}>{centerImg}</button>
                <div class="center-btn__text">
                    <h3 style="color: white; margin: 0">{actionTitle}</h3>
                    <p>Нажмите для<br>использования</p>
                </div>                
            </div>
        </li>
    </ul>		
</nav>
