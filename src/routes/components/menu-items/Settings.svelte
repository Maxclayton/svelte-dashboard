<script>
    import Cog from '../images/cog.png';
    import { scale, slide, blur,} from 'svelte/transition';
    import Quiz from './example.json';
    import Typewriter from 'svelte-typewriter'

    const mathsQuestionCount = Object.keys(Quiz.quiz.maths).length; // Calculate the number of items inside "maths"
    const randomNumber = Math.floor(Math.random() * mathsQuestionCount) + 1;
    var quizPath = null;
    var answerPath = null;
    /**
     * @type {string | null}
     */
    var questionPath = null;

    if (randomNumber === 1) {
        quizPath = Quiz.quiz.maths.q1.options;
        answerPath = Quiz.quiz.maths.q1.answer;
        questionPath = Quiz.quiz.maths.q1.question;
    } else if (randomNumber === 2) {
        quizPath = Quiz.quiz.maths.q2.options;
        answerPath = Quiz.quiz.maths.q2.answer;
        questionPath = Quiz.quiz.maths.q2.question;
    }
    else if (randomNumber === 3) {
        quizPath = Quiz.quiz.maths.q3.options;
        answerPath = Quiz.quiz.maths.q3.answer;
        questionPath = Quiz.quiz.maths.q3.question;
    }

    else {
        quizPath = Quiz.quiz.maths.q4.options;
        answerPath = Quiz.quiz.maths.q4.answer;
        questionPath = Quiz.quiz.maths.q4.question;
    }
    
    const options = quizPath;
    let answer = answerPath;
    let proposedAnswer = '';



</script>

<main>
    <div in:slide={{duration: 1200}} class='middle-container'>
        <div class='middle-item-1'>
            <div class='middle-item-left'>
                <h2>Settings</h2>
                <p>Lorem ipsum dolor sit amet,Lorem ipsum dolor sit  amet</p>
                <button>Contact Us</button>
            </div>
            <div class='middle-item-right'>
                <img src={Cog} in:scale={{duration: 500}} alt='Cog' />
            </div>

        </div>

        <div class='mid-container'>
            <div class='middle-item-2'>
                <div class='middle-item-left'>
                    {questionPath}
                    {#each options as option}
                        <button on:click={() =>
                       {proposedAnswer = option}}
                         >{option}</button>
                        
                     {/each}   
                     <div  class='conditional'>
                        {#if proposedAnswer === answer }
                        <p class='correct-answer' in:blur={{duration: 500}} out:blur={{duration: 200}}>That's correct!</p>
                        {:else if proposedAnswer === ''}
                        <p></p>
                        {:else} 
                        <p in:blur={{duration: 500}} out:blur={{duration: 200}}>Please try again</p>
                        {/if}   
                     </div>
           
                    
                </div>
         
            </div>

            <div class='middle-item-2'>
                <div class='middle-item-left'>
                    {#if proposedAnswer === answer }
                    <Typewriter keepCursorOnFinish={true}><h2>You got it!</h2></Typewriter>
                    {:else if proposedAnswer === ''}
                    <Typewriter keepCursorOnFinish={true}><h2>Try the quiz to the left</h2></Typewriter>
                    {:else} 
                    <Typewriter keepCursorOnFinish={true}><h2>You should probably study some more.</h2></Typewriter>
                    {/if}   
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

    .conditional {
        width: 175px;
        height: 25px;
    }

    .correct-answer {
        color: green;
        font-weight: 500 !important;
    }

   
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
    margin-left: 191px;
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