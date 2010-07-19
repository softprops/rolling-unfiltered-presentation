!SLIDE

pause. what are requests anyway?

!SLIDE

requests == patterns

!SLIDE

Scala <strong>&hearts;</strong>'s matching patterns

    val me = person match {
      case Person("doug", _)  => true
      case _ => false
    }
    
    def act() {
      loop {
        react {
          case Ping => ...
          case Pong => ...
        }
      }
    }
    
!SLIDE

unfiltered <strong>&hearts;</strong>'s matching request patterns

!SLIDE

Scala <strong>&hearts;</strong>'s &fnof;p

!SLIDE

everything is a &fnof;()

!SLIDE

unfiltered <strong>plans</strong> are partial functions

!SLIDE

&fnof;() =>
<div class="hc">
  type ResponseFunction = <br/>&nbsp;&nbsp;HttpServletResponse => HttpServletResponse
</div>
<div class="hc">
  PartialFunction[<strong>HttpServletRequest</strong>, ResponseFunction]
</div>

!SLIDE
  
<div class="hc">/** as a class */
class App extends unfiltered.Planify(<strong>{
  case GET(Path("/", _)) => ResponseString("hola friend")
}</strong>)
</div>

<div class="hc">
/** as a trait */
class App extends Stuff with unfiltered.Plan {
  def filter = <strong>{
    case GET(Path("/", _)) => ResponseString("hola friend")
  }</strong>
}
</div>