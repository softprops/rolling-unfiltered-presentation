!SLIDE

out to sea

!SLIDE

    <deployment-configuration>
      <param-a>foo</param-a>
      <param-b>bleh</parame-b>
      <param-list>
        <parm-c>
      <param-list>
    </deployment-configuration>

!SLIDE

no thanks...

!SLIDE

let's embed*!*

!SLIDE

unfiltered.server.Http

!SLIDE

Jetty under the covers

(for now, others later)
   
!SLIDE

    object Server {
      def main(args: Array[String]) {
        server.Http(8080) filter(Planify { ... }) start
      }
    }
