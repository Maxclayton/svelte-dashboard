<script>
import Fa from 'svelte-fa';
import {faChevronRight} from '@fortawesome/free-solid-svg-icons';
import { onMount, } from 'svelte';
import { fly, slide } from 'svelte/transition';
import Boy from './3D-icons/boy.png';
import Chess from './3D-icons/chess.png'
import Coin from './3D-icons/coin.png'
import Computer from './3D-icons/computer.png'
import Crown from './3D-icons/crown.png'
import Fire from './3D-icons/fire.png'
import Medal from './3D-icons/medal.png'
import Phone from './3D-icons/phone.png'
import Star from './3D-icons/star.png'
import Travel from './3D-icons/travel.png'
import Trophy from './3D-icons/trophy.png'



var transitions = false;

onMount(() => {
    setTimeout(() => {
        transitions = true;
    }, 100);
});


var prodItems = [
        { icon: Boy , title: 'Product number 1' , desc: 'Prod desc', x: 200, duration: 1000 },
        { icon: Chess , title: 'Product number 2' , desc: 'Prod desc', x: -200, duration: 1200  },
        { icon: Coin , title: 'Product number 3' , desc: 'Prod desc', x: 200, duration: 1400  },
        { icon: Computer , title: 'Product number 4' , desc: 'Prod desc', x: -200, duration: 1600  },
        { icon: Crown , title: 'Product number 5' , desc: 'Prod desc', x: 200, duration: 1800  },
        { icon: Fire , title: 'Product number 6' , desc: 'Prod desc', x: -200, duration: 2000  },
        { icon: Medal , title: 'Product number 7' , desc: 'Prod desc', x: 200, duration: 2200  },
        // { icon: Phone , title: 'Product number 8' , desc: 'Prod desc', x: -200, duration: 2400  },
        // { icon: Star , title: 'Product number 9' , desc: 'Prod desc', x: 200, duration: 2600  },
        // { icon: Travel , title: 'Product number 10' , desc: 'Prod desc', x: -200, duration: 2800  },
        // { icon: Trophy , title: 'Product number 11' , desc: 'Prod desc', x: 200, duration: -2800  },

    ];
 

</script>

<main>
<div class="prod-container">
    <div class="prod-title"><div class='color-square'></div>Top Products</div>
    <div class='prod-items prod-top'>
        <div class='prod-item-container'>
            {#each prodItems as prodItem (prodItem.title)}
            {#if transitions}

            <div id='item' in:fly={{ x: prodItem.x, duration: prodItem.duration }} class='prod-items'>
               <div class='prod-sect'><img src={prodItem.icon} alt='alt' /></div>
               <div class='prod-sect'>
                    <h2>{prodItem.title}</h2>
                    <p>{prodItem.desc}</p>
                </div>
               <div class='prod-sect'>
                <Fa icon={faChevronRight} />
               </div>
            </div>
            {/if}
            {/each}
        </div>
    </div>
    <div class='prod-items prod-bottom'>

    </div>
</div>
</main>

<style>

    .prod-container {
        width: auto;
        padding: 25px;
        background-color: #FFF;
        margin-left: 50px;
        border-radius: 6px;
        font-family: 'Poppins';
    }

    .prod-title {
        margin-bottom: 25px;
    }

    .prod-item-container {
        display: flex;
        flex-direction: column;
        gap: 20px;
    }

    .prod-items {
        display: flex;
        flex-direction: row;
        gap: 25px;
        align-items: center;
        padding: 15px;
        transition: .2s;
        border-radius: 6px;
        cursor: pointer;
    }

  #item:hover {
    background-color: #f7f7f7;
  }

    .prod-sect img {
        width: 50px;
    }

    .prod-sect p {
        margin-top: 5px;
        font-size: 12px;
        color: gray;

    }

    @media screen and (max-width: 1000px) {
  .prod-container {
    margin: 0;
  }
    }

</style>