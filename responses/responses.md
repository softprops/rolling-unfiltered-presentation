!SLIDE

&fnof;() in, &fnof;() out

!SLIDE

response <strong>combinators</strong>

!SLIDE

Hi("doug") <strong>~></strong> Im <strong>~></strong> Combinating <strong>~></strong> With("friends")

!SLIDE
<div class='hc'>import javax.servlet.http.{HttpServletResponse => R}
type ResponseFunction = R => R
trait Responder extends ResponseFunction {
  def respond(res: R)
  <strong>def ~> (that: ResponseFunction) = new ChainResponse(
    this andThen that
  )</strong>
}
class ChainResponse(f: ResponseFunction) extends Responder {
  def respond(res: R) = f(res)
}
</div>
!SLIDE
<div class="hc"><span class="ex">ResponseString</span>("what evs")
</div>

!SLIDE
<div class="hc"><span class="ex">Redirect</span>("/")
</div>

!SLIDE
<div class="hc"><span class="ex">Status</span>(200)
<span class="comment">// or</span>
<span class="ex">Ok</span>
<span class="comment">// or</span>
<span class="ex">Status</span>(404)
<span class="comment">// or</span>
<span class="ex">NotFound</span>
<span class="comment">// we named them all*</span>
</div>


!SLIDE
<div class="hc"><span class="ex">Pass</span>*</div>

!SLIDE
why &fnof;n's

!SLIDE
&fnof;n's compose

![compose](responses/debussy.jpg "compose")

!SLIDE
<div class="hc"><span class="ex">ResponseString</span>("what evs") ~> <span class="ex">Ok</span> ~> <span class="ex">ETag</span>(obj.hash) ~>
   <span class="ex">ResponseHeader</span>("x-runtime", TimeFrom(start) :: Nil)
</div>