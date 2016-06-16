---
layout: post
title:  "A Ruby Gem Wrapper for the SPICE Toolkit"
date:   2016-05-25 8:00:35 +0530
categories: gsoc
---

So Google Summer of Code is underway, and I've begun work on my project. This blog post will be a short introduction to 
the project and what it will entail. 

SPICE is a rather large library of FORTRAN routines used for various astronomical calculations involved in using data obtained
during previous space flight missions. To quote the home page of [SPICE][spice] :-

{% highlight none %}

SPICE is focused on solar system geometry. The SPICE system includes a suite of
software, mostly in the form of application program interfaces (APIs), that
customers incorporate in their own application programs to read SPICE data files
and, using those data, compute derived observation geometry such as altitude,
latitude,longitude and lighting angles

{% endhighlight %}

My GSoC project for this summer will be to build a Ruby interface around the native C version of the SPICE Toolkit. SPICE is offered in various languages, primarily
FORTRAN 77, ANSI C, MATLAB and IDL. Using the C toolkit makes it easier to write interface code using just the Ruby C API (it works well because the primary interpreter of Ruby : MRI, is written in C) 

Since FORTRAN usually makes API design very unpleasant for a layman (someone who is more used to using code than writing it) due its limit of 6 characters on member names , the secondary aim of the project is to design a Ruby API to make the usage of this massively-useful-but-in-the-process-fairly-obfuscated more pleasant for an average user. To put it in a nutshell, the task of obtaining say, the co-ordinates of the Sun when viewed from Mars at a certain time will take some calls to SPICE routines that you'd have to search for in the docs. I plan on reducing that to less function call stacking and more sentence like function calls, for this particular something like 

{% highlight ruby %}
Sun.position_at(time, from: :mars)
{% endhighlight %}

The above isn't final but I'm aiming for something that's in the spirit of Ruby.

A major plus point of SPICE is that it is [heavily documented][spice-c-docs], almost exhaustively to my belief. If you'd like to follow this project, it's being hosted at [GitHub][spicerub] , and I'd love any feedback (especially if you decide to clone and test it up). Currently no build automation is available but I'll work on that sometime next week once I put some code up to build :-

The idea is to make this a weekly blog posting habit, so I hope I'll see you next week! 

[spice]: https://naif.jpl.nasa.gov/naif/
[spice-c-docs]: http://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/index.html
[spicerub]: https://github.com/gau27/spice_rub
