<script>
    import Fa from 'svelte-fa';
    import { faBagShopping, faChartLine, faBullseye, faCalendar, faMoneyCheckDollar, faFile, faGear } from '@fortawesome/free-solid-svg-icons';
    import { fly } from 'svelte/transition';
    import { onMount, setContext, } from 'svelte';
    import Overview from './menu-items/Overview.svelte';
    import Products from './menu-items/Products.svelte';
    import Campaigns from './menu-items/Campaigns.svelte';
    import Schedule from './menu-items/Schedule.svelte';
    import Payouts from './menu-items/Payouts.svelte';
    import Statements from './menu-items/Statements.svelte';
    import Settings from './menu-items/Settings.svelte';

    import Logo from './images/logo.png'

     var active = 'Overview';

    const activeContext = setContext('active', active);

    var transitions = false
    var menuItems = [
        { icon: faChartLine, title: 'Overview', delayS: 200, x: -200},
        { icon: faBagShopping, title: 'Products', delayS: 225, x: -250},
        { icon: faBullseye, title: 'Campaigns', delayS: 250, x: -300},
        { icon: faCalendar, title: 'Schedule', delayS: 275, x: -350},
        { icon: faMoneyCheckDollar, title: 'Payouts', delayS: 300, x: -400},
        { icon: faFile, title: 'Statements', delayS: 325, x: -450},
        { icon: faGear, title: 'Settings', delayS: 350, x: -500},
    ];
 

    onMount(() => {
    setTimeout(() => {
        transitions = true;
    }, 100);
});

    /**
     * @param {string} title
     */
function changeActive(title) {
    active = title;
}




</script>

<main>
<div class='menu-container'>
    <div class='logo-container'>
        <img src={Logo} alt='Logo' />
    </div>
    <div class='menu-item-container'>
        <h3>Admin Tools</h3>
        {#each menuItems as menuItem (menuItem.title)}
        {#if transitions}

        <button on:click={() => changeActive(menuItem.title)} transition:fly={{ y: menuItem.x, delay:menuItem.delayS }} class='menu-item {active === menuItem.title ? "active" : ""}'>
            <div class='icon-container {active === menuItem.title ? "activeIcon" : ""}'>
                    <Fa icon={menuItem.icon} />
                </div>
                {menuItem.title}
        </button>
        {/if}
      {/each}
    </div>
    <div class='bottom-cta'>
        <p>{active}Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore</p>
        <button>Download Now</button>
    </div>
</div>
{#if active === 'Overview'}
<Overview />
{:else if active === 'Products'}
<Products />
{:else if active === 'Campaigns'}
<Campaigns />
{:else if active === 'Schedule'}
<Schedule />
{:else if active === 'Payouts'}
<Payouts />
{:else if active === 'Statements'}
<Statements />
{:else if active === 'Settings'}
<Settings />
{/if}

</main>

<style>
    @import url('https://fonts.googleapis.com/css2?family=Inter:wght@200;400;800&family=Poppins:ital,wght@0,300;0,400;1,400&family=Roboto:wght@300;400&display=swap');

    main {
        display: flex;
        flex-direction: row;
        gap: 25px;
    }

    .menu-container {
        width: 275px;
        background-color: #1e54e2;
        display: flex;
        flex-direction: column;
        align-items: center;
        padding: 10px 5px 30px 5px;
        border-radius: 10px;
        font-family: 'Roboto', sans-serif;
    }

    .menu-item-container h3 {
        font-weight: 100;
    }

    .logo-container img {
        width: 100px;
    }

    .menu-item-container {
        margin-top: 15px;
        display: flex;
        flex-direction: column;
        gap: 20px;
        height: 500px;
        align-items: normal;
        color: #FFF;
    }

    .menu-item-container button {
      border: none;
      background-color: #1e54e2;

    }

    .menu-item {
        display: flex;
        flex-direction: row;
        color: #fff;
        width: 200px;
        gap: 25px;
        height: 45px;
        align-items: center;
        font-size: 20px;
        border-radius: 12px;
        transition: .2s;
        padding: 0px 15px 0px 15px;
        cursor: pointer;
        border-right: 5px solid #1e54e2;

    }
    
    .menu-item:hover {
        background-color: #fff;
        color: #000;
        border-right: 5px solid #00dbff;
    }

    .menu-item:hover > .icon-container {
        color: #1e54e2;
    }

    .bottom-cta {
        width: 200px;
        background-color: #3066fb;
        padding: 20px 15px 15px 15px;
        color: #becdfa;
        border-radius: 10px;
        text-align: center;
        margin-top: 50px;
        font-size: 16px;
    }

    .bottom-cta button {
        background-color: #00d2fa;
        color: #fff;
        border: none;
        width: 150px;
        height: 50px;
        border-radius: 6px;
        cursor: pointer;
        transition: .3s;
        margin-top: 25px;
    }

    .bottom-cta button:hover {
        background-color: #5300fa;
    }

    .active {
        background-color: #fff !important;
        color: #000;
        border-right: 5px solid #00dbff !important;
    }

    .activeIcon {
        color: #1e54e2 !important;
    } 

    @media screen and (max-width: 1000px) {
       main {
        flex-direction: column;
       }

       .menu-container {
        width: auto;
       }
    }


</style>