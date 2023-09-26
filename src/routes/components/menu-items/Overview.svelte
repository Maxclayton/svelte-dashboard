<script>
// @ts-nocheck

    import Laptop from '../images/laptop.jpg';
    import { getContext } from 'svelte';
    import {  slide, scale} from 'svelte/transition';
    import { scaleLinear } from 'd3-scale';
	import points from './data.js';
    import Countup from "svelte-countup";


	const yTicks = [0, 2, 4, 6, 8];
	const xTicks = [1980, 1990, 2000, 2010, 2015, 20];
	const padding = { top: 20, right: 15, bottom: 20, left: 25 };

	let width = 500;
	let height = 200;

	$: xScale = scaleLinear()
		.domain([minX, maxX])
		.range([padding.left, width - padding.right]);

	$: yScale = scaleLinear()
		.domain([Math.min.apply(null, yTicks), Math.max.apply(null, yTicks)])
		.range([height - padding.bottom, padding.top]);

	$: minX = points[0].x;
	$: maxX = points[points.length - 1].x;
	$: path = `M${points.map((p) => `${xScale(p.x)},${yScale(p.y)}`).join('L')}`;
	$: area = `${path}L${xScale(maxX)},${yScale(0)}L${xScale(minX)},${yScale(0)}Z`;

	/**
     * @param {{ toString: () => string; }} tick
     */
	function formatMobile(tick) {
		return "'" + tick.toString().slice(-2);
	}

    const active = getContext('active');

</script>

<main>
    <div in:slide={{duration: 1200}} class='middle-container'>
        <div class='middle-item-1'>
            <div class='middle-item-left'>
                <h2>Overview</h2>
                <p>Lorem ipsum dolor sit amet,Lorem ipsum dolor sit  amet</p>
                <button>Contact Us</button>
            </div>
            <div class='middle-item-right'>
                <img src={Laptop} in:scale={{duration: 500}} alt='laptop' />
            </div>

        </div>

        <div class='mid-container'>
            <div class='middle-item-2'>
                <div class='middle-item-left'>
                    <h2>1980-2015</h2>
                </div>
         
            </div>

            <div class='middle-item-2'>
                <div class='middle-item-left'>
                    <h2 class='pos-h2'>
                        <Countup
                         value={75} 
                         duration={1000}
                         />%

                    </h2>
                </div>
         
            </div>

        </div>

        <div class='middle-item-3'>
            <div class="chart" bind:clientWidth={width} bind:clientHeight={height}>
                <svg>
                    <!-- y axis -->
                    <g class="axis y-axis" transform="translate(0, {padding.top})">
                        {#each yTicks as tick}
                            <g class="tick tick-{tick}" transform="translate(0, {yScale(tick) - padding.bottom})">
                                <line x2="100%" />
                                <text y="-4">{tick}</text>
                            </g>
                        {/each}
                    </g>
            
                    <!-- x axis -->
                    <g class="axis x-axis">
                        {#each xTicks as tick}
                            <g class="tick tick-{tick}" transform="translate({xScale(tick)},{height})">
                                <line y1="-{height}" y2="-{padding.bottom}" x1="0" x2="0" />
                                <text y="-2">{width > 380 ? tick : formatMobile(tick)}</text>
                            </g>
                        {/each}
                    </g>
            
                    <!-- data -->
                    <path class="path-area" d={area} />
                    <path class="path-line" d={path} />
                </svg>
            </div>

        </div>

  
    </div>
</main>

<style>

    @import url('https://fonts.googleapis.com/css2?family=Inter:wght@200;400;800&family=Poppins:ital,wght@0,300;0,400;1,400&family=Roboto:wght@300;400&display=swap');

    .middle-container {
        display: flex;
        flex-direction: column;
        gap: 25px;
    }

    .mid-container {
        display: flex;
        flex-direction: row;
        gap: 25px;
    }

    .middle-item-1 {
        background-color: #00d2fa;
        color: white;
        display: flex;
        flex-direction: row;
        gap: 75px;
        padding: 25px 25px 0 25px;
        font-family: 'Roboto';
        border-radius: 10px;
        /* width: 600px; */
    }

    .middle-item-2 {
        background-color: #FFF;
        color: black;
        display: flex;
        flex-direction: row;
        gap: 75px;
        padding: 25px 25px 0 25px;
        font-family: 'Roboto';
        border-radius: 10px;
        /* width: 262px; */
        justify-content: center;
        align-items: center;
    }


    .middle-item-3 {
        background-color: #FFF;
        color: #000;
        display: flex;
        flex-direction: row;
        gap: 75px;
        padding: 25px 25px 25px 25px;
        font-family: 'Roboto';
        border-radius: 10px;
        /* width: 600px; */
    }

    .pos-h2 {
    font-size: 65px !important;
    color:  green;
    font-family: 'Poppins';
}

    .middle-container {
        display: flex;
    }

    .middle-item-1 img{
        width: 225px;
        position: absolute;
        margin-left: -18px;
        margin-top: -41px;
    }

    .middle-item-left {
        display: flex;
        flex-direction: column;
        gap: 20px;
        margin-bottom: 35px;
        width: 200px;
    }



    .middle-item-left h2 {
        font-size: 25px;
    }

    .middle-item-left p {
        font-size: 15px;
        font-weight: 100;
    }

    .middle-item-1 button {
        background-color: white;
        border: none;
        width: 150px;
        height: 50px;
        color: #1e54e2;
        font-size: 18px;
        font-weight:bold;
        border-radius: 6px;
        transition: .2s;
        cursor: pointer;
    }

    .middle-item-1 button:hover {
        background-color: #1e54e2;
        color: white;
    }

    .chart,
	h2,
	p {
		width: 100%;
		max-width: 500px;
		margin-left: auto;
		margin-right: auto;
	}

	svg {
		position: relative;
		width: 100%;
		height: 200px;
		overflow: visible;
	}

	.tick {
		font-size: 0.725em;
		font-weight: 200;
	}

	.tick line {
		stroke: #888;
		stroke-dasharray: 2;
	}

	.tick text {
		fill: #888;
		text-anchor: start;
	}

	.tick.tick-0 line {
		stroke-dasharray: 0;
	}

	.x-axis .tick text {
		text-anchor: middle;
	}

	.path-line {
		fill: none;
		stroke: rgb(0, 100, 100);
		stroke-linejoin: round;
		stroke-linecap: round;
		stroke-width: 2;
	}

	.path-area {
		fill: rgba(0, 100, 100, 0.2);
	}


    @media screen and (max-width: 1000px) {
   .pos-h2 {
    font-size: 35px !important;
   }

   .middle-item-1 {
    flex-direction: column;
   }

   .middle-item-1 img {
    width: 150px;
    margin-left: 120px;
    margin-top: -152px;
   }

   .middle-item-left {
    width: auto;
   }
    }



</style>