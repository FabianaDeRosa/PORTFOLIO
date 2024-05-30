<svelte:head>
    <title>My Portfolio</title>
    <meta name="Portfolio works" content="A collection of my works">
</svelte:head>


<div>
    <h2>About <br> my portfolio</h2>
    <iframe src="https://www.canva.com/design/DAGGtKsqjuE/5RT59mvdwIX6F-NIQW0mYg/view?embed" title="" allowfullscreen frameborder="0"></iframe>
</div>


<style lang="scss">

    div{
        align-self: center;
        display: grid;
        justify-items: center;
        grid-template-columns:repeat(auto-fit, minmax(70ch, 1fr));
        margin-bottom: 2.5rem;
        margin-top: 4rem;

        h2{
            font-weight: 700;
            font-family: 'CactusJack';
            font-size: 5rem;
            margin-bottom: 7rem;
            text-align: center;
            margin-top: 0;
        }
        
        iframe{
                padding: 0;
                width: 70% ;
                height: 381px;
                border: none; 
                margin: 0;
                
            }
    }

    @media screen and (max-width: 600px) {
        div{
            grid-template-columns:repeat(auto-fit, minmax(60ch, 1fr));

            iframe{
                padding: 0;
                width: 77.8% ;
                height: 252px;
            }
        }
    
}
</style>


