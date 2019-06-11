<script>
    let quote;

    function loadNewQuote(){
        quote = fetch('https://quotesondesign.com/wp-json/posts?filter%5Borderby%5D=rand&filter%5Bposts_per_page%5D=1')
            .then(res => res.json())
            .then(data => data[0].content);
    }

    loadNewQuote();
</script>

<style>
    h1{
        color: red;
    }
</style>

<h1>
<slot>Default heading</slot>
</h1>
{#await quote then value}
    {@html value}
{/await}

<button on:click={loadNewQuote}>Load</button>
