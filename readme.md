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