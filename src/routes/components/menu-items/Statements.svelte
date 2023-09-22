<script>
    import Doc from '../images/doc.png';
    import { getContext } from 'svelte';
    import { scale, slide} from 'svelte/transition';

    const active = getContext('active');

</script>

<main>
      <div in:slide={{duration: 1200}} class='middle-container'>
        <div class='middle-item-1'>
            <div class='middle-item-left'>
                <h2>Statements</h2>
                <p>Lorem ipsum dolor sit amet,Lorem ipsum dolor sit  amet</p>
                <button>Contact Us</button>
            </div>
            <div class='middle-item-right'>
                <img src={Doc} in:scale={{duration: 500}} alt='laptop' />
            </div>

        </div>

        <div class='mid-container'>
            <div class='middle-item-2'>
                <div class='middle-item-left'>
                    <h2>Lorem ipsum dolor sit amet</h2>
                </div>
         
            </div>

            <div class='middle-item-2'>
                <div class='middle-item-left'>
                    <h2>Lorem ipsum dolor sit amet</h2>
                </div>
         
            </div>

        </div>

        <div class='middle-item-3'>
            <h2>Lorem ipsum dolor sit ametorem ipsum dolor sit ametorem
                 ipsum dolor sit ametorem ipsum dolor sit ametorem ipsum
                  dolor sit ametorem ipsum dolor sit amet
                  orem ipsum dolor sit ametorem ipsum dolor sit ametorem 
                  ipsum dolor sitorem ipsum dolor sit ametorem ipsum dolor 
                  sit amet amet</h2>

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
        width: 737px;
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

    @media screen and (max-width: 1000px) {


   .middle-item-1 {
    flex-direction: column;
   }

   .middle-item-1 img {
    width: 150px;
    margin-left: 203px;
    margin-top: -152px;
   }

   .middle-item-left {
    width: auto;
   }

   .middle-item-3 {
        width: auto;
    }
    }


</style>