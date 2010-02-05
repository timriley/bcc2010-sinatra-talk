!SLIDE smbullets incremental

# Sinatra

* Web application library & DSL
* In Ruby
* But it's not Rails
* Not MVC
* Centred around RESTful HTTP actions
* Fast
* Minimal code, minimal effort
* Minimal opinion
* __Fun!__

!SLIDE subsection

# Getting Started #

!SLIDE smaller commandline incremental

	$ gem install sinatra

	$ ruby my_app.rb
	== Sinatra/0.9.4 has taken the stage on 4567 for development with backup from Mongrel

!SLIDE

	@@@ruby
	require 'rubygems'
	require 'sinatra'

	get '/' do
		'Hello World!'
	end
	
!SLIDE

	@@@ ruby
	get '/barcamp' do
		'Hello BarCamp'
	end

!SLIDE

	@@@ ruby
	get '/hello/:name' do
		"Hello #{params[:name]}"
	end
	
!SLIDE small

	@@@ ruby
	get '/time' do
		erb "The time is <%= Time.now.strftime('%h:%m') %>"
	end

!SLIDE center

![Frank, from http://studentweb.hunter.cuny.edu/~cderoma/](frank1.jpg)