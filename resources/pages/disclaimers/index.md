---
transition: fade
layout: section
---

# Disclaimers

<!-- 

I only have one disclaimer about the things I'm about to talk about.

Mostly, there are gaps in documentation today 
- we need more learning materials on proper derived data, including resources, patterns, (in and outside of ember)
- we need to actually implement Starbeam for Ember

For those that stick to only the what the official documentation recommends, this may all feel experimental and out of reach.

and to help mitigate that feeling, I've been working on some learning materials and tutorials. 

I want to close *all the gaps* -- I'll try to answer anyone's questions, provide help, you name it.

And the point of all of this is to solve real problems more efficiently, 
while also reducing cognitive load on everyone writing their apps. 

-->


---
transition: fade
layout: center
---
<div class="related-note">Disclaimers</div>

# All APIs shown by libraries I provide will have codemods  

<div v-click class="disclaimer-note">
  No one will be left behind.
</div>

<div v-click class="disclaimer-note">
    Also ember-source@3.28 will be supported for the foreseeable and unforeseeable future.
</div>

<!-- 
It's extremely important that there are easy migration paths within the community.

!!click 

Programming is hard, and some migration paths are not (and have not been) so easy.

The overall goal for everything I'm working on for and around this talk, Resources, etc 
is to be a _polyfill_ for Starbeam -- 
I ultimately want Starbeam to be *the* Resource implementation we use, 
but in this talk, I demonstrate with the library `ember-resources`, because you can install and use it today.  

Any behavioral difference between my library, `ember-resources` 
and Starbeam is considered a bug.

!! click

I'm committing on keeping support for ember-source@3.28 for as long as I can. 
I want to make sure that folks still on v3 can use the patterns coming in the future.

(afaik, I think everything publicly available about Polaris is available and stable for use in 3.28)

--

Anywho, getting back to it...
-->




