!SLIDE subsection

# Advanced Stuff

!SLIDE center

![Haml](haml.gif)

!SLIDE

# Haml

	@@@ haml
	#profile
	  .left.column
	    #date= print_date
	    #address= current_user.address
	  .right.column
	    #email= current_user.email
	    #bio= current_user.bio
	
!SLIDE center

![Sass](sass.gif)
	
!SLIDE

# Sass

	@@@ sass
	h1
	  height: 118px
	  margin-top: 1em

	.tagline
	  font-size: 26px
	  text-align: right

!SLIDE center

![Rack logo](rack_logo.png)

!SLIDE small

# Rack::Test

	@@@ ruby
	def test_it_says_hello_world
		get '/'
		assert last_response.ok?
		assert_equal 'Hello World', last_response.body
	end

!SLIDE bullets

# Sinatra::Base

## Enabling web interfaces to *