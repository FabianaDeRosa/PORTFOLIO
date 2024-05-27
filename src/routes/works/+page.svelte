<svelte:head>
    <title>My Works</title>
    <meta name="Portfolio works" content="A collection of my works">
</svelte:head>

<script>
    const categories = ["all", "digital art", "ux/ui", "front-end","3d","photography","game design","animation","generative art & sound design","others"];
    import works from "$lib/JSON/works.json"
	import WorkCard from "./WorkCard.svelte";
    import Button from "./Button.svelte";
    
    let selected = "all";
    const filterSelection = (e) => selected = e.target.dataset.name;
    //$: firstItems = works.img.slice(0, 0);
</script>



<div id="all-items-wrapper">

    <div id="filter-btn">
        <Button>
            {#each categories as category}
                <button class:active={selected === category} 
                                class="btn" 
                                data-name={category} 
                                on:click={filterSelection}>
                    {category}
                </button>
            {/each}
        </Button>
    </div>
    
    <WorkCard>
        <div id="works-wrapper">
            {#each works as {id, title, keyword, img, sub}}	
			{#if selected === "all"}
            <section>
                <article class="show hide">
                    <a href="/works/{id-1}"><div style="background-image:url({img});"></div></a>
                   <h2>{title}</h2>
                   <p>{sub}</p>
                </article>
            </section>
			{:else}
            <section>
                <article class:show={selected === keyword} class="hide">
                    <a href="/works/{id-1}"><div style="background-image:url({img});"></div></a>
                   <h2>{title}</h2>
                   <p>{sub}</p>
                </article>
            </section>
            
			{/if}
		{/each}
        </div>

        
	</WorkCard>

</div>


<style lang="scss">

    #all-items-wrapper{
        display: grid;
        grid-template-rows: min-content auto;
        padding-top: 5rem;
        

        #filter-btn{
            padding-bottom: 4rem;

            button{
                border: 1px solid;
                width: fit-content;
                padding: .5rem 1rem;
                cursor: pointer;
                font-family: "DMMono";
                font-weight: 200;
                text-transform: uppercase;

                &:hover{
                    background-color: map-get($colors, secondary );
                    color: map-get($colors, primary );
                    border: 1px solid map-get($colors, secondary );
                }
            }
        }

        #works-wrapper{
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(40ch, 1fr));
            justify-content: center;

        .show{
        display: grid;
        grid-template-rows: min-content min-content;
        padding: 1rem;


        div{
            height: 25ch;
            background-size: cover;
            background-repeat: no-repeat;
            background-position: center;

            &:hover{
            cursor: pointer;
            transform: scale(1.05);
         
            }
        }

        h2{
            text-transform: uppercase;
            font-weight: 300;
            margin: 0;
            margin-top: 1rem;
            font-size: 1.1rem;
        }

        p{
            font-weight: 200;
            margin: 0;
            font-size: .8rem;
            margin-top: .2rem;
            font-style: italic;
        }

        &:hover{
           h2 {
            color: map-get($colors, secondary );
           }
         }
        
        }

         
     
        }
    }

    .btn:active,
    .active {
	background-color: map-get($colors, secondary );
	color: map-get($colors, primary );

    }

    .hide{
        display: none;
    }

    

</style>