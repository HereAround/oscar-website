---
layout: page
title: To be sorted
---

### Getting a GAP prompt

If you are a GAP user and have started OSCAR in a Julia session, you can at any time switch back and forth between the Julia prompt
and a GAP prompt, by using the command `GAP.prompt()`:

<pre>
<span style="color: green">julia></span> x = 1
1

<span style="color: green">julia></span> GAP.prompt()
<span style="color: blue">gap></span> Julia.x;
1
<span style="color: blue">gap></span> G := SymmetricGroup(3);
Sym( [ 1 .. 3 ] )
<span style="color: blue">gap></span> quit;   # or press Ctrl-D

<span style="color: green">julia></span> GAP.Globals.G
GAP: Sym( [ 1 .. 3 ] )
</pre>
