<script>
    let quote = fetch('https://quotesondesign.com/wp-json/posts?filter%5Borderby%5D=rand&filter%5Bposts_per_page%5D=1')
            .then(res => res.json())
            .then(data => data[0].content);
</script>

<style>
    h1{
        color: red;
    }
</style>

<h1>Random Quote!</h1>
{#await quote}
    loading
{:then value}
    {@html value}
{:catch}
    Error
{/await}
