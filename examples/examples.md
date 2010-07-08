Inline

    import unfiltered._

    object Server {
      def main(args: Array[String]) {
        server.Http(8080) filter(Planify {
          case _ => ResponseString("hola friend")
        }) start
      }
    }

!SLIDE

Reusbale

    import unfiltered._

    class Authd extends unfiltered.Planify({
      case GET(Path("/", BasicAuth(creds, _))) => creds match {
        case ("doug", "d0ug") => ResponseString("hola " + id) ~> Ok
        case _ => WWWAuthenticate("Basic realm=\"/\"") ~> Unauthorized
      }
    })

    object Server {
      def main(args: Array[String]) {
        server.Http(8080).filter(new Authd).start
      }
    }