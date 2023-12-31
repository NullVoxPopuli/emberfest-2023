--- 
transition: fade
layout: center
---

# Components?

<div v-click>

```jsx
const AComponent = resource(() => {
    // "Component State"
    let count = cell(0);
    let increment = () => count.current++; 

    // template-only / presentational / stateless component
    return <>
        {count}<br>
        <button onClick={increment}>
          increment
        </button>
    </>;
}); 

```

</div>

<!-- 

Can a resource also be a component?

kind of..

!! click

In React, it may look like this.

returning a template-only (or presentational, or stateless) component as their value, using the closed over function within the resource _as_ the state.


_however_...

The main thing is that every framework already has legit component implementations,
and those implementations are good at what they do.

-->

--- 
transition: fade
---

<small class="related-note">Components?</small>

# We can do it

```gjs
import { resource, cell } from 'ember-resources';
import { on } from '@ember/modifier';

const Demo = resource(() => {
  let count = cell(0);
  let increment = () => count.current++;
  
  return (
    <template>
      {{count}}<br>
  
      <button {{on 'click' increment}}>Add</button>
    </template>
  );
});

<template>
  {{#let (Demo) as |whatHaveIDone|}}
    <whatHaveIDone />
  {{/let}}
</template>
```

<div class="corner-br">
<QRCode size="450" value="https://limber.glimdown.com/edit?c=MQAgSgpgzg9grgJwMbRAQygOm5kSYC2ADjAHYSkAuUA-AFB0B8IgOAQCa8CIUSAlhZV5RqIAO4QEEbjBBFJMJEjhF%2BAEzG9KACzFaI2iSAMBPPPAA2qgDRG9p1b1WkA5JW6UYRIzO29SAaxBeADNbCFMoLQtVTEBcAgY6AANkgHMAKygQc14ANwg6XmIYBDcAbxBJWEQUGxRzcxAAXxBghEIQZwgCACMJAFpKzhQoZwBuAqKSkHKyJpa2gg6AAS7ehAB6AhgHYP4EMYZ8UmEQABEumQBeCughiAAKe4BKEEvmUroQLP0zOCpXvAQer3AAMT3GX3MPz8SEkBAEAOer2Y%2BD%2BlEwSgQkioAGocRCQJ8bpREKQQPciV8ADyULpEcxoWmMSlfaalVFURqNKndBDMr4s6ndOCUDxk0qlWbOJDZJD%2BZxBUiwroCLmMACCqlUVPWwtFZH5rJ1tOIDKZRPBdEalroNLpZogholwChbnu5y2LwwIAAPqItIyABJoPIASVOZAgPq5LKp-qDIYg4cjIHWjB5fNj8cowbDEfIqadpXWrq5GaLLp%2B7ouXsyfoDOcTyfI0caWYbuaT%2BakaaJEpL%2BhjxvtjMdSWSQA&format=glimdown"></QRcode>
</div>

<!--

We can do it, too!

You can see, however, that at the bottom, of the code snippet, 
in order to get this to work, 
you have to invoke the resource like a function
and then render its return value.

-->


--- 
transition: fade
---

<small class="related-note">Components?</small>

# We can do it

```gjs
import { resource, cell } from 'ember-resources';
import { on } from '@ember/modifier';

const Demo = resource(() => {
  let count = cell(0);
  let increment = () => count.current++;
  
  return (
    <template>
      {{count}}<br>
  
      <button {{on 'click' increment}}>Add</button>
    </template>
  );
});

<template>
  <Demo />
</template>
```

<div class="corner-br">
<QRCode size="450" value="https://limber.glimdown.com/edit?c=MQAgSgpgzg9grgJwMbRAQygOm5kSYC2ADjAHYSkAuUA-AFB0B8IgOAQCa8CIUSAlhZV5RqIAO4QEEbjBBFJMJEjhF%2BAEzG9KACzFaI2iSAMBPPPAA2qgDRG9p1b1WkA5JW6UYRIzO29SAaxBeADNbCFMoLQtVTEBcAgY6AANkgHMAKygQc14ANwg6XmIYBDcAbxBJWEQUGxRzcxAAXxBghEIQZwgCACMJAFpKzhQoZwBuAqKSkHKyJpa2gg6AAS7ehAB6AhgHYP4EMYZ8UmEQABEumQBeCughiAAKe4BKEEvmUroQLP0zOCpXvAQer3AAMT3GX3MPz8SEkBAEAOer2Y%2BD%2BlEwSgQkioAGocRCQJ8bpREKQQPciV8ADyULpEcxoWmMSlfaalVFURqNKndBDMr4s6ndOCUDxk0qlWbOJDZJD%2BZxBUiwroCLmMACCqlUVPWwtFZH5rJ1tOIDKZRPBdEalroNLpZogholwChbnu5y2LwwIAAPqItIyABJoPIASVOZAgPq5LKp-qDIYg4cjIHWjB5fNj8cowbDEfIqadpXWrq5GaLLp%2B7ouXsyfoDOcTyfI0caWYbuaT%2BakaaJEpL%2BhjxvtjMdSWSQA&format=glimdown"></QRcode>
</div>

<!--

But!

this is only a component-manager implementation away
(or one focussed night away)
from actually working as a component.


And it really shows how useful the `<template>` syntax is.

I mean, this wouldn't at all be possible with classic two-file syntax.

-->

--- 
transition: fade
---

<img src="/pages/main/science.jpg">

<!--

This is one of my favorite quotes about doing goofy things.


But science is pretty fun, so let's keep going.

-->

--- 
transition: fade
layout: center
---

<small class="related-note">Components?</small>

<video 
  controls 
  loop autoplay
  class="component-video"
  src="/pages/main/examples/recordings/resources-as-components.webm"></video>

<div v-click class="component-managers">
<QRCode size="400" value="https://github.com/emberjs/rfcs/blob/master/text/0213-custom-components.md">Component Managers</QRCode>
</div>

<style>
    .component-video {
        position: fixed;
        right: 0;
        bottom: 0;
        top: 0;
    }
    .component-managers {
        position:fixed;
        left: 1rem;
        bottom: 1rem;
        background: black;
        border-radius: 0.5rem;
        box-shadow: 0 0 10px rgba(0,0,0,0.8);
        transition: all 0.2s;
    }
</style>

<!-- 

Here is what the demo looks like.

You can see that, today, the resource still needs to be invoked like a function,
and that if we only invoke it once, each time we render the component returned from the resource,
they share the same state.

I don't know if this has any use cases,
but an important thing to note is that this 
is a function that returns a component.

!! click

we could adapt this to a component manager
and have the invocation happen automatically for us 
creating a new closure around the returned component,
but... I don't know if it's all worth it. 

This isn't something I want to ship -- I guess unless people *really* want it.

anyway... 
-->

--- 
transition: fade
layout: center
---

<small class="related-note">Components?</small>

# Components are not primitives



<!--

I mentioned this a while back, and I want to revisit this idea.

Components are not primitives.

-->

--- 
transition: fade
layout: center
---

<div class="slide-category">Components are not primitives</div> 
<small class="related-note">Components?</small>

# The Primitives

<v-clicks class="big-list">

- values
- helpers / functions
- resources

</v-clicks>


<style>
   .logos img { 
        position: fixed;
    }

    .logos .ember  { top: 1rem; left: 1rem; width: 250px; }
    .logos .react  { top: 7rem; left: 10rem; width: 250px; }
    .logos .preact { top: 14rem; left: 15rem; width: 250px;}
    .logos .vue    { top: 5rem; left: 20rem; width: 250px;}
    .logos .svelte { top: 10rem; left: 25rem; width: 250px;}

</style>
<div class="logos">
<img class="ember" v-click src="/pages/logos/ember-e-circle-icon-4c.svg" alt="the ember 'e' logo" />
<img class="react" v-click src="/pages/logos/react.svg" alt="the React logo" />
<img class="preact" v-click src="/pages/logos/preact.png" alt="the Preact logo" />
<img class="vue" v-click src="/pages/logos/vue.svg" alt="the Vue logo" />
<img class="svelte" v-click src="/pages/logos/svelte.png" alt="the svelte logo" />
</div>

<!--

So re-capping the primitives,


We know from Ember Octane, and now that we've renamed some of the primitives that Octane introduced,
we have:

!!click

values.

!! click

functions

!! click

and now, resources, which represent a value bound to a lifetime.
and rationionalize class-based-helpers, modifiers, services.


...

These can all be authored and shared anywhere.

And that's the main goal of Starbeam.
We can write our application logic once, 
data-fetching, UI logic, modifiers... anything reactive...


and use it 


!!click 

in not only Ember, but  

!!click

React,

!!click Preact, 

!!click Vue, 

!!click Svelte, you name it.


It's super exciting, 
because most other frameworks don't have modifiers,  
and none of them have resources, as far as I know.

-->

--- 
transition: fade
layout: center
---

<small class="related-note">Components?</small>

# Components are not primitives


<!--

Components _wrap_ the primitives.

Components are refactoring boundaries.

They are containers for organizing higher-level concepts.


-->
