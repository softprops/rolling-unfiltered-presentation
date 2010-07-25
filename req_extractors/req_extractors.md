!SLIDE

abstraction thru extraction 

!SLIDE

request extractors

!SLIDE

extractors?

![extractors](req_extractors/inception.jpg "extractors")


!SLIDE
<div class="hc">
<span class="comment">// the ghost in the compiler</span>
def unapply(x: X): Y
</div>

<div class="hc">
<span class="comment">// imagine this...</span>
subject match { 
  case SomeExtractor(y) => Some(y) 
  case _ => None 
}
</div>

<div class="hc">
<span class="comment">// as this in reverse (returns Some(y) or None)</span>
SomeExtractor.unapply(subject) 
</div>

!SLIDE
<div class="hc"><span class="comment">// the ghost in unfiltered's compiler</span>
def unapply(x: <strong>X</strong>): (<strong>Y</strong>, HttpServletRequest)    
</div>
!SLIDE
<div class="hc"><span class="ex">GET</span>(_), <span class="ex">POST</span>(_), <span class="ex">PUT</span>(_), <span class="ex">DELETE</span>(_), <span class="ex">HEAD</span>(_)
</div>
!SLIDE
<div class="hc"><span class="ex">Path</span>(<strong>"/hello"</strong>, _)
</div>
!SLIDE
<div class="hc">Path(<span class="ex">Seg</span>(<strong>"have" :: "a" :: what :: when :: Nil</strong>), _) => {
  case _ => ResponseString(
    "oh really? having a %s on %s" format(what, when)
  )
}
</div>
!SLIDE
<div class="hc"><span class="ex">Params</span>(<strong>params</strong>, _) <span class="comment">// Map[String, Seq[String]] </span>
</div>
!SLIDE
<div class="hc"><span class="ex">InStream</span>(<strong>in</strong>, _)
</div>
!SLIDE
<div class="hc"><span class="ex">Reader</span>(<strong>r</strong>, _)
</div>
!SLIDE
<div class="hc"><span class="ex">BasicAuth</span>(<strong>creds</strong>, _) => {
  case ("jane", "j@n3") => <span class="comment">// jane stuff</span>
  case ("jim", "j1m") =>   <span class="comment">// jim stuff</span>
  case _ =>                <span class="comment">// default stuff</span>
}
</div>
!SLIDE
<div class="hc"><span class="ex">Accepts</span>(<strong>fmt</strong>, _) => {
  case 'json => <span class="comment">// json stuff</span>
  case 'xml =>  <span class="comment">// xml stuff</span>
  case _ =>     <span class="comment">// otherwise default stuff</span>
}
</div>
!SLIDE
It's just a convention.