!SLIDE
    import unfiltered._
    
    class Authd extends unfiltered.Planify({
      case GET(Path("/", BasicAuth(creds, _))) => creds match {
        case ("doug", "d0ug") => 
          ResponseString("~treasure map~") ~> Ok
        case _ => 
          WWWAuthenticate("Basic realm=\"/\"") ~> Unauthorized
      }
    })

!SLIDE
    import unfiltered._

    object Server {
      def main(args: Array[String]) {
        server.Http(8080).filter(unfiltered.Planify {
          case _ => "\('.')~"
        }).start
      }
    }