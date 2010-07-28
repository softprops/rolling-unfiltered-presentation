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
        server.Http(8080)
          .filter(Planify { ... })
          .filter(Planify { ... })
          .resources(getClass.getResouce("path/to/rsrc"))
          .start
      }
    }

!SLIDE
    package treasure
    class Maps extends unfiltered.Planify({
      case GET(Path("/", BasicAuth(creds, _))) => 
        creds match {
          case ("doug", "d0ug") => 
            ResponseString("~treasure map~") ~> Ok
          case _ => 
            WWWAuthenticate("Basic realm=\"/\"") ~> 
              Unauthorized
        }
    })

!SLIDE
    package treasure
    object Server {
      def main(args: Array[String]) {
        server.Http(8080).filter(new Maps).start
      }
    }

!SLIDE
but, if you really need to...

!SLIDE

    <?xml version="1.0" encoding="utf8"?>
    <!DOCTYPE web-app
    PUBLIC "-//Sun Microsystems, Inc.//DTD Web Application 2.3//EN"
    "http://java.sun.com/dtd/web-app_2_3.dtd">
    <web-app>
      <filter>
        <filter-name>Maps</filter-name>
        <filter-class>treasure.Maps</filter-class>
      </filter>
      <filter-mapping>
        <filter-name>Maps</filter-name>
        <url-pattern>/*</url-pattern>
      </filter-mapping>
    </web-app>
