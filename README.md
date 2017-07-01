### spring-boot-demo

This project shows that breakpoints don't work in intellij community edition,
when spring-boot:run is launched with the `fork` option set to true.

Note that the spring boot plugin implicitly sets `fork` to true, if you try to
pass vm parameters such as `-Dspring.profiles.active=dev`.  

Steps to reproduce:

1. Add a breakpoint in `HelloController#index`
1. Open "maven projects" view in intellij
1. Open "spring-boot" goals, under Plugins
1. Right-click on the spring-boot:run goal, and select "debug"
1. Open http://localhost:8080/ in browser. 
   Observe: Breakpoint doesn't work.
1. Shut down app and try to launch again. 
   Observe: Error because the old process is still running, and port 8080 isn't free.
