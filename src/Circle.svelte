<script>        
    export let arr;
    export let emoji;

    export let nav = '';
    export let btns = '';
    
    export let centerImg = '👋'; 
    export const cross = "❌";
    export const croossTitle = 'Закрыть'

	export let itemValue = 'greeting';

    export let actionTitle = 'Поздороваться';

	export const setCenterImg = (value) => {
        return (value === 'cross') ? cross : emoji[value].pic        
	}

    export const setActionTitle = (value) => {        
        return (value === 'cross') ? croossTitle : emoji[value].title;        
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

	export const mouseHandler = (event) => {
		itemValue = event.target.value;
		centerImg = setCenterImg(itemValue);
        actionTitle = setActionTitle(itemValue)
	}

    export const showNav = (arr, emoji)=> {        
        arr.forEach((item) => {
            debugger;
            let markup = `
            <li class="${item} slice">            
                <button class="circle-menu item" value=${item} >${emoji[item].pic}</button>
            </li>
            `
            nav.insertAdjacentHTML('afterBegin', markup);
        })                        
    }

    document.addEventListener('DOMContentLoaded', () => {
       nav = document.getElementById('navList');    
       showNav(arr, emoji);
       btns = document.querySelectorAll('.item');
       btns.forEach((btn) => {
           btn.addEventListener('mouseover', (e) => {
               mouseHandler(e);
       })
    })      
    }, false);        
</script>


<nav id='nav'>
    <div class="settings" on:click={()=>console.log('settings')}><h2>⚙️</h2></div>			
    <ul id='navList' class="circle-menu">             
        <li class="cross slice">            
            <button class="circle-menu item" value='cross'>{cross}</button>
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
