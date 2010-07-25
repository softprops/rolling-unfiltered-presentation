!SLIDE
(raises hand)

How do we test?

!SLIDE

simple

    >sbt ~test

!SLIDE

having nice complements 

is a plus


<span class="ex">:/(</span>":)"<span class="ex">)</span> 
  
!SLIDE

    trait Served extends Specification {
      shareVariables()

      import unfiltered.server._
      def setup: (Server => Server)
      val port = 9090
      lazy val server = setup(new Http(port))
      val host = :/("localhost", port)

      doBeforeSpec { server.start() }
      doAfterSpec { server.stop() }
    }

!SLIDE
    object BasicSpec extends Specification 
      with unfiltered.spec.Served {
      import unfiltered.request.{Path => UFPath}
      
      def setup = { _.filter(unfiltered.Planify {
        case GET(UFPath("/", _)) => ResponseString("test")
      })}
  
      "A Server" should {
        "respond to requests" in {
          Http(host as_str) must_=="test"
        }
      }
    }

!SLIDE
    object ToasterSpec extends Specification with 
      unfiltered.spec.Served {
      def setup = { _.filter(unfiltered.Planify {
        case _ => JsonContent ~> ResponseString(
          """{"bread":"toasted"}""")
      }) }

      "Toaster" should {
        "toast bread" in {
          val (body, headers) = Http(host >+ { r => 
            (r as_str, r >:> { h => h }) })
           headers must havePair(
             ("Content-Type" -> Set(
               "application/json; charset=utf-8")))
          body must_=="""{"bread":"toasted"}"""
        }
      }
    }