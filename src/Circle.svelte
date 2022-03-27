<script>
  import { onMount } from "svelte";
  export let arr;
  export let emoji;

  export let navList = "";
  export let items = "";
  export let centerBtn = "";

  export let centerImg = "👋";
  export const cross = "❌";
  export const croossTitle = "Закрыть";

  export let itemValue = "greeting";

  export let actionTitle = "Поздороваться";

  export const setCenterImg = (value) => {
    return value === "cross" ? cross : emoji[value].pic;
  };

  export const setActionTitle = (value) => {
    return value === "cross" ? croossTitle : emoji[value].title;
  };

  export const showActionValue = (e, value) => {
    if (e.which === 1) {
      console.log("use action", value);
    } else if (e.which == 3) {
      centerBtn.addEventListener(
        "contextmenu",
        (event) => event.preventDefault(),
        false
      );
      console.log("delete action", value);
      centerBtn.removeEventListener(
        "contextmenu",
        (event) => event.preventDefault(),
        false
      );
      return false;
    }
  };

  export const mouseHandler = (event) => {
    itemValue = event.target.value;
    centerImg = setCenterImg(itemValue);
    actionTitle = setActionTitle(itemValue);
  };

  export const showNav = (arr, emoji) => {
    arr.forEach((item) => {
      let markup = `
            <li class="${item} slice">            
                <button class="circle-menu item" value=${item} >${emoji[item].pic}</button>
            </li>
            `;
      navList.insertAdjacentHTML("afterBegin", markup);
    });
  };

  onMount(() => {
    showNav(arr, emoji);
    items = navList.children;
    for (let i = 0; i < items.length; i++) {
      items[i].childNodes[1]?.addEventListener("mouseover", (e) => {
        mouseHandler(e);
      });
    }
  });
</script>

<nav>
  <div class="settings" on:click={() => console.log("settings")}>
    <h2>⚙️</h2>
  </div>
  <ul class="circle-menu" bind:this={navList}>
    <li class="cross slice">
      <!-- svelte-ignore a11y-mouse-events-have-key-events -->
      <button
        class="circle-menu item"
        on:mouseover={(e) => mouseHandler(e)}
        value="cross">{cross}</button
      >
    </li>
    <li class="center circle-menu">
      <div class="center-btn">
        <button
          class="center-btn__btn"
          bind:this={centerBtn}
          on:mousedown={(e) => showActionValue(e, itemValue)}
          >{centerImg}</button
        >
        <div class="center-btn__text">
          <h3 style="color: white; margin: 0">{actionTitle}</h3>
          <p>Нажмите для<br />использования</p>
        </div>
      </div>
    </li>
  </ul>
</nav>
