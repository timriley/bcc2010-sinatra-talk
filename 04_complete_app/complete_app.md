!SLIDE

# Enough with the hello worlds!

!SLIDE subsection

# A Complete App

!SLIDE bullets

* Database/ORM integration
* App configuration
* Form handling

!SLIDE

	@@@ ruby
	require 'rubygems'
	require 'sinatra'
	require 'active_record'

!SLIDE
	
	@@@ ruby
	class Talk < ActiveRecord::Base
		validates_presence_of :title
	end
	
!SLIDE code

# database/config.yml

	@@@ ruby
	production: &main
	  adapter: sqlite3
	  database: db/talks.sqlite3
	  pool: 5
	  timeout: 5000
	
	development:
		<<: *main

!SLIDE smaller

	@@@ ruby
	configure do
	  db_config = YAML.load_file('config/database.yml')

	  ActiveRecord::Base.establish_connection(
			db_config[ENV['RACK_ENV'] || 'production']
		)
	end

!SLIDE small

	@@@ ruby
	
	get '/' do
		@talks = Talk.all(:order => 'created_at DESC')
		erb :home
	end
	
!SLIDE code

# views/home.erb

	@@@ html
	<ol id="talks">
		<% @talks.each do |talk| %>
			<li><%= talk.title %></li>
		<% end %>
	</ul>
	
!SLIDE code small

# views/home.erb

	@@@ html
	<div id="new-talk">
		<form action="/talks" method="post">
			<label class="title">
				Title:
				<input name="title" type="text"/>
			</label>
		</form>
	</div>
	
!SLIDE small

	@@@ ruby
	post '/talks' do
		talk = Talk.new(:title => params[:title])
		talk.save
		redirect '/'
	end
	
!SLIDE smaller

	@@@ ruby
	before do
		headers "Content-Type" => "text/html; charset=utf-8"
	end

!SLIDE center

![Sinatra sign, from http://www.earlyvegas.com/images/old_caesars_palace_las_vegas_1.jpg](vegas.jpg)