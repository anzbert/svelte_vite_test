<script lang="ts">
  import Textbox1 from "./textbox1.svelte";
  export let date: Date;
  export let tags: Array<string>;
  export let title: string;

  const dateOptions: Intl.DateTimeFormatOptions = {
    weekday: "long",
    year: "numeric",
    month: "long",
    day: "numeric",
    hourCycle: "h24",
  };
</script>

<Textbox1>
  <div class="header">
    <h1 class="title">{title}</h1>
    <h3 class="date">
      {date.toLocaleDateString("en-AU", dateOptions)}
    </h3>
  </div>

  <hr />

  <div class="tags">
    {#each tags as tag}
      {#if tag !== "#all"}
        <div class="tag">{tag}</div>
      {/if}
    {/each}
  </div>

  <slot>
    <!-- blog content -->
  </slot>

  <div class="footer" />
</Textbox1>

<style>
  .date {
    margin-top: 0.5em;
    font-size: 1rem;
  }
  .header {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    align-items: end;
  }
  .tags {
    display: flex;
    gap: min(1.5vw, 1rem);
  }
  .tag {
    background-color: var(--gray3);
    color: var(--blue1);
    border-radius: 5px;
    padding: 0.3em 0.6em;
    font-size: 0.8rem;
    pointer-events: none;
  }
  .footer {
    height: 3rem;
  }
</style>
