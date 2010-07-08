&fnof;() in, &fnof;() out

!SLIDE

response <strong>combinators</strong>

!SLIDE

Hi("doug") <strong>~></strong> Im <strong>~></strong> Combinating <strong>~></strong> With("friends")

!SLIDE

<div class="hc">
  <span class="ex">ResponseString</span>("what evs")
</div>

!SLIDE

<div class="hc">
  <span class="ex">Redirect</span>("/")
</div>

!SLIDE

<div class="hc">
  <span class="ex">Status</span>(200)
  <span class="comment">// or</span>
  <span class="ex">Ok</span>
</div>

!SLIDE

<div class="hc">
  <span class="ex">Pass</span>
</div>

!SLIDE

&fnof;n's compose

!SLIDE

<div class="hc">
  <span class="ex">ResponseString</span>("what evs") ~> <span class="ex">Ok</span>
</div>