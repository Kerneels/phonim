# Introduction #

In order to get the job done of making vim speak, a few different solutions are explained. Each solution presents  it's own unique set of challenges and advantages and range greatly in implementation difficulty levels.

The main reason for exploring multiple solutions is to try and find the best option without forgetting perhaps about another solution should the best option at the time eventually turn up some unsolvable problems. A second reason for exploring alternatives is to try and accommodate many end users.

Each solution has it's own main wiki page from where more pages are linked.

## Solutions ##

Each solution is designated a keyword reflecting the main technology essential for producing speech. The set of solutions are:

  * Java.
  * JAWS.
  * NVDA.
  * GVIM.

### Java ###

This is the most exciting solution. It promises to be truly cross platform, the most responsive, the cheapest for the end user, but unfortunately the hardest to implement. It's main dependency and essential component is the Java runtime.

For more on this solution, and to see why it is so exciting, see the wiki page [Java](Java.md).

### JAWS ###

This solution is Windows only due to it's reliance on JAWS and hence significantly expensive if the end user does not own JAWS already. The good news is that the JAWS solution is the simplest and already has a working, but very alpha implementation.

For more on the JAWS solution, see the [JAWS](JAWS.md) wiki page.

### NVDA ###

This solution is also Windows only, just like the JAWS solution, but it is free since NVDA is freely available. This solution functions very similar to the JAWS solution, but needs a bit more work.

For more info on this solution, and to see why it needs more work see the wiki page [NVDA](NVDA.md).

### GVIM ###

This solution involves altering the vim source code so that vim can expose more information to the accessibility technology running on the end user's machine. This solution was originally my first choice, but because gvim is written in C and draws it's screen directly (does not make use of an editor control) and is essentially a single thread of control, I abandoned this solution in favour of one of the otheres.

Having said that, I still think that this solution is a real possibility and would like to explore it further.
> For more info on this solution, see the wiki page [GVIM](GVIM.md).