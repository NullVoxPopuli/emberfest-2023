--- 
transition: fade
layout: center
---

# Load data anywhere without any downsides\*

<div style="position: fixed; bottom: 2rem">* With a good abstraction</div>

<!-- 

!! click

As a quick disclaimer this is still in the work, still being figured out, and will hopefully be the foundation of 
the new routing system.

-->


--- 
transition: fade
layout: center
---

<div style="display: flex; gap: 2rem">
<h2 v-click style="border: 3px solid; border-radius: 100%; width: 350px; height: 350px; text-align: center; line-height: 350px">
    Routes
</h2>

<h2 v-click style="border: 3px solid; border-radius: 100%; width: 350px; height: 350px; text-align: center; line-height: 350px">
    Not Routes
</h2>
</div>

<!-- 
In ember, there are a couple places to load components:

!! click

- in routes

!! click

- and not in routes 

loading data outside of routes is immensely useful when you would otherwise be forced to drill props through countless layers of components. 

Resources can help eliminate the end-user-perceived difference between loading data in components and routes.
-->

--- 
transition: fade
layout: center
---

<img v-click src="/pages/waterfall.png">

<!--

Both places, routes and not in routes today allow for an easy problem to run in to 

!!click

The request waterfall, where large chunks of your app are delayed until particular data loads.

While this isn't a problem unique to resources -- it's a problem with naiive loading of *primary* data within components,
we can solve it.
-->

--- 
transition: fade
layout: two-cols
---

# So what's the solution?

::left::

```gjs
import { Request } from 'someplace';

<template>
  {{#let (Request '/blogs/') as |blogs|}}
      Available properties:
       - {{blog.records}}
       - {{blog.error}}
       - {{blog.isLoading}}
       - {{blog.isSuccess}}
       - {{blog.isError}}
       - {{blog.hasRan}}

      Available methods:
       - <button {{on 'click' blog.retry}}>
          Retry
        </button>
  {{/let}}
</template>
```

::right::

```gjs
import { Request } from 'someplace';

export default class Demo extends Component {
    @use blogs = Request('/blogs/');

    <template>
      Available properties:
       - {{this.blog.records}}
       - {{this.blog.error}}
       - {{this.blog.isLoading}}
       - {{this.blog.isSuccess}}
       - {{this.blog.isError}}
       - {{this.blog.hasRan}}

      Available methods:
       - <button {{on 'click' this.blog.retry}}>
           Retry
         </button>
    </template>
}
```

<!-- 
What do we do?

We have the ability to have good developer ergonomics.
In this example, we have the exact same abstraction being suitable different styles of component authoring.

But this abstraction needs some help to prevent waterfalls.

-->

--- 
transition: fade
layout: two-cols
---

# So what's the solution?


::left::

<div v-click>

```gjs {1,4}
import { HoistedRequest } from 'someplace';

<template>
  {{#let (HoistedRequest '/blogs/') as |blogs|}}
      Available properties:
       - {{blog.records}}
       - {{blog.error}}
       - {{blog.isLoading}}
       - {{blog.isSuccess}}
       - {{blog.isError}}
       - {{blog.hasRan}}

      Available methods:
       - <button {{on 'click' blog.retry}}>
          Retry
        </button>
  {{/let}}
</template>
```

</div>

::right::

<div v-click>

```gjs {1,4}
import { HoistedRequest } from 'someplace';

export default class Demo extends Component {
    @use blogs = HoistedRequest('/blogs/');

    <template>
      Available properties:
       - {{this.blog.records}}
       - {{this.blog.error}}
       - {{this.blog.isLoading}}
       - {{this.blog.isSuccess}}
       - {{this.blog.isError}}
       - {{this.blog.hasRan}}

      Available methods:
       - <button {{on 'click' this.blog.retry}}>
           Retry
         </button>
    </template>
}
```

</div>

<!--

I kind of see two paths to solving this:
- a runtime path,
- and a hybrid runtime and build time path

The runtime path would use a backing service, or maybe even solely ember-data's Request Manager for a shared unified request cache, so that multiple components trying to access the same URL don't double up on work. 

!! click
!! click

The buildtime path is a bit more inlvolved, but we'd want to *also* have this backed by a service, but handle some build time determine metadata about which requests can be loaded together -- without waiting for rendering in order to start a request.

The possibilities are basically limitless, and we're in a good spot for experimenting with solutions along these lines.

-->

