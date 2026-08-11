::: {.list .quarto-listing-default}

<% let activeCycle = null; %>
<% for (const item of items) { %>
<% const startsCycle = item.cycle && item.cycle !== activeCycle; %>
<% if (startsCycle) { activeCycle = item.cycle; } %>

::: {.quarto-post .image-right <%= metadataAttrs(item) %>}

<% if (startsCycle) { %>
<h2 class="session-cycle-heading no-anchor"><%= item.cycle %></h2>
<% if (item.description) { %>

```{=html}
<div class="delink session-cycle-description">
```

<%= item.description %>

```{=html}
</div>
```

<% } %>
<% } %>

::: {.body}

<h3 class="no-anchor listing-title"><a href="<%- item.path %>" class="no-external"><%= item.title %></a></h3>

<% if (item.subtitle) { %>
<div class="listing-subtitle"><%= item.subtitle %></div>
<% } %>

<% if (item.categories) { %>

```{=html}
<div class="listing-categories">
<% for (const category of item.categories) { %>
<div class="listing-category" onclick="window.quartoListingCategory('<%= utils.b64encode(category) %>'); return false;"><%= category %></div>
<% } %>
</div>
```

<% } %>

:::

::: {.metadata}

<% if (item.date) { %>
<div class="listing-date"><%= item.date %></div>
<% } %>

<% if (item.author) { %>
<div class="listing-author"><%= item.author %></div>
<% } %>

:::

:::

<% } %>

:::
