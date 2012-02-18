web-development-aalto
=====================

Additional material for students of Aalto University course t-110.5140 "Network Application Frameworks"

Rich-client Web Development
---------------------------

See [Developing With Web Standards](http://www.456bereastreet.com/lab/developing_with_web_standards/), especially chapters 4 and 6.

For jQuery, there are many tutorials, for instance, [this one](http://docs.jquery.com/Tutorials:Getting_Started_with_jQuery).

RESTful Server Development
--------------------------

In the example, we used [Scala](http://www.scala-lang.org/) programming language, the
[Scalatra](https://github.com/scalatra/scalatra) web framework and [SBT](https://github.com/harrah/xsbt/wiki) build tool
for building and running.

We also used [IntelliJ IDEA](http://www.jetbrains.com/idea/) for editing and compiling the code.
You need the IDEA Scala plugin for Scala projects. You can install this plugin using IDEA Settings. Instead of IDEA,
you can of course use any other editor or IDE, such as VIM or Eclipse (with Scala plugin).

PartyBlastr
-----------

Current version running at [PartyBlastr](http://partyblastr.com).

Current source code and development instructions available at [GitHub](http://github.com/raimohanska/partyblastr).

Architectural alternatives
--------------------------

- Server-side templating
  + "Easy to start" because you can mix content and logic on the same "page"
  - UI and backend logic get easily mixed leading to spaghetti code
  - No abstraction layers
  - Testing difficult (can not test individual pieces)
  + Especially with PHP: hosting is trivial because mod-php tends to be installed on Apache
- Server-side frameworks
  + "Full solution" comprising server-side and client-side stuff
  + Desktop-like programming: Hide the client-server separation to some extent (good or bad?)
  - Wicket (Components with separate HTML and Java code)
  - Google Web Toolkit (Components that produce HTML, Java2JS compilation)
  - Rails (Full solution. MVC separates concerns, includes persistence with MySQL etc)
  - Scalability issues: server-side is stateful => not trivial to deploy parallel server nodes
  - Performance issues: lots of roundtrips with AJAX
  - Does not enforce UI/Service separation => ties business logic and UI together
- Rich client + REST
  + Clear architectural split between client and server
    - multiple clients can be implemented
    - client/server implementation technology choices are independent
      - Server : Java / .NET / Ruby / Scala / ..
      - Client : HTML+JS / Flash / Mobile / Desktop
  + Separate testing/development of frontend and backend possible (mock the other side in test)
  + Fat client can minimize client-server traffic, reducing server load and roundtrips for maximum performance
  + Takes the HTTP infrastructure to full use: caching reduces server load
  + Scalability good : stateless server nodes can be deployed in parallel
  + Javascript community is very active, producing innovative new libs and frameworks all the time
  - REST is not suitable for everything
    - Push to client (instead of polling)
    - Content streaming (video, audio)
  - With HTML frontend
    - Must use Javascript
    - Lots of JS code to test (must test a lot of code in different browsers)

Server-side programming languages
---------------------------------

This is opinionated :)

- Java
  + JRE => hosting, perfomance, field-proven runtime
  + Library, Documentation availability
  + Large developer base
  + Development tools (Eclipse, IDEA)
  - Retarded development compared to .NET for example
- Ruby
  + More modern language, supports FP better
  + Rails, Sinatra frameworks support rapid development
  - Performance not so good (not JRE based)
  - Dynamic typing
- PHP
  + Easy to start (documentation, can embed logic into HTML)
  + Apache support => easy deployment
  - Not a very nice programming language
  - Oriented towards server-side templating => not a real alternative as a RESTful server lang
- .NET
  + Good tools, documentation
  + Improving constantly (esp. compared to Java), new languages introduced etc (F#)
  + Large developer base
  - Dev machines and servers must be Windows (practically)
- Haskell
  + Modern, expressive language
  + Frameworks for RESTful web services: Yesod, Snap
  - Not well known, tiny developer base (compared to..)
  - No IDE support (not a killer in this scale)
  - Non JRE => hosting more difficult
- Scala
  + Modern, expressive language
  + JRE => hosting, perfomance, field-proven runtime
  + Java libraries can be used
  + Nice Scala frameworks (Scalatra, lift-json)
  + Transition from Java/.NET is easier than Haskell, Clojure, Ruby
  - IDE support not so fantastic (improving though)
  - Binary instability (dependency on Scala version)
  - Framework/library maturity (new stuff is introduced rapidly, doesn't get stable before may already be replaced by something else)
  + In active developement, both libs&lang => intreresting environment for developers

- Why Scala for Partyblastr?
  - Elegant lang, functional programming
  - Deploy to JRE => Hosting available : Heroku, Google App Engine
  - Not too foreign for students who know Java
