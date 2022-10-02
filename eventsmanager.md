## Standardkopfzeile für Veranstaltungsliste
```html
<ul class="events">
```


## Veranstaltungsliste Listelement
```html
<li class="eventcard">
    <a href="#_EVENTURL">
        {has_att_label}<span class="eventcard-label">#_ATT{label}</span>{/has_att_label}
        <div class="eventcard-img">#_EVENTIMAGE</div>
<section class="eventcard-content">
        <h2>#_EVENTNAME</h2>
        <p>#_EVENTEXCERPT</p>
<hr>

<section class="eventcard-aside">
	<p class="price"><span class="aside-head">Termin</span><br>#_EVENTDATES</p>
 	{has_location}<p class="location"><span class="aside-head">Schwierigkeit</span><br>#_ATT{skills}</p>{/has_location}
</section>

<section class="eventcard-aside">
        <p class="price"><span class="aside-head">Preis</span><br>#_EVENTPRICERANGE</p>
        {has_location}<p class="location"><span class="aside-head">Location</span><br>#_LOCATIONNAME</p>{/has_location}
</section>
</section>
<a class="link" href="#_EVENTURL" target="_self"><div class="ast-button">Details...</div></a>
    </a>
</li>
```

## Fußzeile für Veranstaltungsliste
```html
</ul>
```

## Veranstalgungsdetailseite
```html
<div style="float:right; margin:0px 0px 15px 15px;">#_LOCATIONMAP</div>
<p>#_EVENTEXCERPT</p>
<aside class="event-aside">
<p><span class="aside-head">Termine</span><br/>#_EVENTDATES</p>
<p><span class="aside-head">Location</span><br/>{has_location}#_LOCATIONNAME{/has_location}</p>
</aside>

<p>
	<strong class="aside-head">Schwierigkeit</strong>
	<br/>#_ATT{skills}
</p>
<hr>
<br style="clear:both" />
#_EVENTNOTES
Freie Plätze: #_AVAILABLESPACES
<br> <br/>

{has_bookings}
<h3>Buchen</h3>
#_BOOKINGFORM
{/has_bookings}

<script>
var equipment = document.getElementsByClassName("equipment");
var ski = document.querySelectorAll('[class*="ski_"]');
var attendees = document.getElementById("em-ticket-spaces-1");

window.onload = function OnLoad() {
    ski.forEach(hide);
}

window.addEventListener('change', (event) => {
console.log(event);

if(event.srcElement.value.match(/Skitourenski/)) {
var parent = event.srcElement.closest(".em-attendee-fields");
var ski = parent.querySelectorAll('[class*="ski_"]');

if (event.srcElement.checked) {
    ski.forEach(show);
  } else {
    ski.forEach(hide);
  }

}

})



function hide(item){
item.style.cssText = 'display:none !important';
}
function show(item){
item.style.cssText = 'display:block !important';
}
</script>
```

## CSS
```css
/* Event Detail Page */
.event header{
	display: flex;
	margin:0;
	padding: 0;
	flex-wrap: wrap;
	background: var(--off-white);
}

.event header .post-thumb{
	width: 40%;
	overflow: hidden;
}

.event header img{
	height: auto;
	width: 100%;
}

.event .ast-single-post-order{
	margin: 0 !important;
	width: 60%;
	display: flex;
	justify-content: center;
	align-items: center;
}
.event .ast-single-post-order h1{
	font-weight: bold;
	color: var(--main-color);
	padding: 2rem;
}

.event .event-aside{
	display: flex;
	width: 100%;
	justify-content: space-between;
}

.event .event-aside p:nth-child(1){
	width: 40%;
}
.event .event-aside p:nth-child(2){
	width: 60%;
}

.event .event-categories{
	list-style: none;
	display: flex;
	margin: 0;
}

.event .event-categories a{
	margin-right: 1rem;
	text-transform: uppercase;
	padding: 0.25em 1em;
}
.event .event-categories a:hover{
	background: var(--main-color);
	color: white !important;
	padding: 0.25em 1em;
	transition: all 0.4s ease-in-out;
}

@media (max-width: 414px) {
	.event header{
		flex-direction: column;
	}
	.event header .post-thumb{
		width: 100%;
	}
	.event .ast-single-post-order{
		width: 100%;
		padding: 2rem 0rem;
	}

	.event .event-aside p:nth-child(1){
	width: 50%;
}
.event .event-aside p:nth-child(2){
	width: 50%;
}
}

.em-booking-form-details{
	width: 100%;
}

.em-booking-form label{
	width: 100%;
}

div .em-booking-login{
	display: none;
	padding:0;
	margin:0;
	border-left: none;
}


div .em-booking-login label{
	width: 100%;
}
.em-booking-form span.input-group{
	display: block;
	margin:0;
}
.em-booking-form span.input-group input {
	margin: 0;
}

/* Events Overview Page */
.events{
	list-style: none;
	display: flex;
	margin: 0;
	flex-wrap: wrap;
	justify-content: space-between;
}

.eventcard{
	background: var(--bright-blue);
	width: 360px;
	height: 100%;
	margin-bottom: 4rem;
	transform: scale(1);
-webkit-box-shadow: 10px 10px 20px 0px rgba(0,0,0,0.1);
-moz-box-shadow: 10px 10px 20px 0px rgba(0,0,0,0.1);
box-shadow: 10px 10px 20px 0px rgba(0,0,0,0.1);
	transition: all 0.4s ease-in-out;
}

.eventcard:hover{
	transform: scale(1.02);
	-webkit-box-shadow: 10px 10px 40px 0px rgba(0,0,0,0.1);
-moz-box-shadow: 10px 10px 40px 0px rgba(0,0,0,0.1);
box-shadow: 10px 10px 40px 0px rgba(0,0,0,0.1);
}

.eventcard-label{
	position: absolute;
	background: var(--main-color);
	color: white;
	padding: 0.25rem 1rem;
	margin: 1rem;
	text-transform: uppercase;
}

.eventcard img{
	width: 100%;
}

.eventcard-img{
	height: 180px;
	overflow: hidden;
}

.eventcard-content{
	padding: 1rem;
}

.eventcard-content h2{
	font-weight: bold;
	color: var(--main-color);
	margin-top: 2rem;
}
.eventcard-aside{
	display: flex;
} 

.eventcard-aside .price{
	width: 30%;
	margin-right: 2rem;
}
.aside-head{
	text-transform: uppercase;
	font-weight: bold;
	color: var(--main-color);
}

.eventcard .link{
	text-align: right;
}
