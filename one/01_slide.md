!SLIDE 
# Web templates
## HAML and SASS
### johan.lundahl@jayway.com

!SLIDE bullets incremental
# -> HTML #
* HAML
* Slim
* Jade
* Scaml
* Serenade

!SLIDE bullets incremental
# -> CSS #
* SASS - Syntactically Awesome Stylesheets
* SCSS - Sassy CSS
* LESS - Just less

!SLIDE bullets incremental
# Why?
* DRY code - less to write
* Easier to read?
* More fun
* Generation style

!SLIDE
# HAML
## HTML Abstraction Markup Language

!SLIDE
## Plain text
	@@@haml
	%gee
	  %whiz
	    Wow this is cool!

->
	@@@html
	<gee>
	  <whiz>
	    Wow this is cool!
	  </whiz>
	</gee>

!SLIDE
## Include HTML or JSP/eRuby
	@@@haml
	%html
		%body
			<div id="blah">Blah!</div>
			<%= expression =>

->
	@@@html
	<html>
	  <body>
	    <div id="blah">Blah!</div>
	    <%= expression =>
	  </body>
	</html>

!SLIDE
## Attributes - as a Ruby hash
	@@@haml
	%script{type: "text/javascript",
    src: "javascripts/script_#{2 + 7}"}

->
	@@@html
	<script src='javascripts/script_9'
		type='text/javascript'></script>

!SLIDE
## ...or alternatively
	@@@haml
	%script(type="text/javascript"
    src="javascripts/script_#{2 + 7}")

->
	@@@html
	<script src='javascripts/script_9'
		type='text/javascript'></script>

!SLIDE
## You could write...
	@@@haml
	%element(class="class" id="id") content

->
	@@@html
	<element class='class' id='id'>content
	</element>

!SLIDE
## ...but this is easier
	@@@haml
	%element.class#id content

->
	@@@html
	<element class='class' id='id'>content
	</element>

!SLIDE
## Div is default
	@@@haml
	.class#id content

->
	@@@html
	<div class='class' id='id'>content</div>

!SLIDE
## Ruby evaluation
	@@@haml
	#time
		= Time.now

->
	@@@html
	<div id='time'>
		2012-02-05 19:16:01 +0100
	</div>

!SLIDE
## Ruby evaluation - without insertion
	@@@haml
	- (42...47).each do |i|
		- if i.even?
			.even= i
		- else
			.odd= i

->
	@@@html
	<div class='even'>42</div>
	<div class='odd'>43</div>
	<div class='even'>44</div>
	<div class='odd'>45</div>
	<div class='even'>46</div>

!SLIDE
# SASS
## Syntactically Awesome StyleSheets

!SLIDE bullets incremental
## Extends CSS with

* Functions
* Variables
* Nesting
* Mixins
* Inheritance

!SLIDE
## Functions and variables
	@@@css
	$color-1: #111111
	$color-2: #555555

	h1
		color: mix($color-1, $color-2, 25%)

->
	@@@css
	h1 {
	  color: #444444;
	}

!SLIDE
## Nesting
	@@@sass
	table.hl
	  td.ln
	    text-align: right
	  font:
	    size: 1.2em
->
	@@@css
	table.hl {
	  font-size: 1.2em;
	}
	table.hl td.ln {
	  text-align: right;
	}

!SLIDE
## Mixins
	@@@sass
	@mixin left($dist)
		td, th
			float: left
			margin-left: $dist

	#data
		@include left(10px)
->
	@@@css
	#data td, #data th {
	  float: left;
	  margin-left: 10px;
	}

!SLIDE
## Selector inheritance
	@@@sass
	.error
	  border: 1px #f00
	.badError
	  @extend .error
	  border-width: 3px
->
	@@@css
	.error, .badError {
	  border: 1px red;
	  background: #ffdddd;
	}
	.badError {
	  border-width: 3px;
	}

!SLIDE
# Sinatra
## The easiest way to try it out

!SLIDE
## Sinatra (1/2)
	@@@ruby
	require 'sinatra'

	get '/' do
		@hello = 'Hello world!!!'
		haml :index
	end

	get '/styles.css' do
		sass :styles
	end

	__END__

!SLIDE
## Sinatra (2/2)
	@@@ruby
	@@ index
	%html
		%head
			%link{:rel => "stylesheet",
				:href => "styles.css",
				:type => "text/css"}
		%body
			%div.title= @hello

	@@ styles
	.title
		font:
			size: 3em

!SLIDE bullets incremental
# What about the rest?
* Jade - Node
* Scaml - Scala
* SCSS - CSS-like SASS
* LESS - Almost as SCSS

!SLIDE bullets incremental
# What about Java?
* JHaml
* SassyBarista
* Ant scripts
* Scaml
* JRuby (Use Java in Ruby)
* Red Bridge (Use Ruby in Java)

!SLIDE
# Questions?

!SLIDE
# Thank you!

### johan.lundahl@jayway.com