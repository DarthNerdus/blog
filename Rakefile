# Standard library
require 'rake'
require 'yaml'
require 'fileutils'

# Load the configuration file
config = YAML.load_file("_config.yml")

# Set "rake preview" as default task
task :default => :preview

# rake draft title="Testing" template="link" meta="http://google.com"
desc "Create a draft in _drafts [title, template, meta]"
task :draft do
  title     = ENV["title"] || nil
  if ENV["template"].nil?
    template = "_templates/#{config["post"]["template"]}"
  else
    template  = "_templates/#{ENV["template"]}.md"
  end
  meta      = ENV["meta"] || nil
  extension = config["post"]["extension"] || nil
  editor    = config["editor"] || nil

  if title.nil? or title.empty?
    raise "Please add a title to your post."
  end

  filename = "#{title.gsub(/(\'|\!|\?|\:|\s\z)/,"").gsub(/\s/,"-").downcase}.#{extension}"
  content  = File.read(template)

  if File.exists?("_drafts/#{filename}")
    raise "The draft already exists."
  else
    parsed_content = "#{content.sub("title:", "title: \"#{title}\"")}"
    parsed_content = "#{parsed_content.sub("meta:", "meta: \"#{meta}\"")}" if not meta.nil?
    open("_drafts/#{filename}", 'w') do |draft|
      draft.puts parsed_content
    end
    # File.write("_posts/#{filename}", parsed_content)
    puts "#{filename} was created."

    if editor && !editor.nil?
      sleep 2
      system "#{editor} _drafts/#{filename}"
    end
  end
end

# rake publish post="testing"
desc "Move a post from _drafts to _posts"
task :publish do
  post      = ENV["post"] || nil
  extension = config["post"]["extension"]
  filename = "#{post}.#{extension}"

  if post.nil? or post.empty?
    Dir["_drafts/*.#{extension}"].each do |filename|
      list = File.basename(filename, ".*")
      puts list
    end
  elsif File.exists?("_drafts/#{filename}")
    date     = Time.now.strftime("%Y-%m-%d")
    time     = Time.now.strftime("%Y-%m-%d %X %z")

    content = File.read("_drafts/#{filename}")
    parsed_content = "#{content.sub("date: 2100-01-01", "date: #{time}")}"
    open("_drafts/#{filename}", 'w') do |draft|
      draft.puts parsed_content
    end

    if File.exists?("_posts/#{date}-#{filename}")
      raise "That post is already published."
    else
      FileUtils.mv("_drafts/#{filename}", "_posts/#{date}-#{filename}")
      puts "#{filename} was moved to _posts."

      system "git stash"
      system "git add _posts/#{date}-#{filename}"
      system "git commit -m \"Published #{date}-#{filename}\""
      system "git stash apply"
    end
  else
    raise "That draft does not exist." if not File.exists?("_drafts/#{filename}")
  end
end

# rake server_push
desc "Publish files into the local server directory /var/www/public"
task :server_push do
  puts "Building site"
  system "jekyll build --config _config.yml,_config-server.yml"
  system "/bin/rm -r /var/www/public_old"
  system "mv /var/www/public /var/www/public_old"
  system "mv public /var/www/"
  puts "Put public folder at /var/www/public"
end
  

# rake preview
desc "Launch a preview of the site in the browser [drafts (true/false)]"
task :preview do
  drafts = ENV["drafts"] || "false"

  Thread.new do
    puts "Launching server..."
    sleep 2
  end

  if drafts == "false"
    system "jekyll serve -w -H jesseread.net -P 8888 --config _config.yml,_config-dev.yml"
  else
    system "jekyll serve --future -w -D -H jesseread.net -P 8888 --config _config.yml,_config-dev.yml"
  end
end

# rake deploy
desc "Deploy website to configured s3 bucket"
task :deploy_s3 do
  puts "Building site"
  system "jekyll build"
  puts "\n--> Syncing media files..."
  sh "s3cmd sync --acl-public --exclude '*.*' --include 'assets/*' --include 'images/*' --add-header=\"Expires: Sat, 20 Nov 2020 18:46:39 GMT\" --add-header=\"Cache-Control: max-age=6048000\"  public/ s3://jesseread.net"

  puts "\n--> Syncing Javascript and CSS assets next (Cache: expire in 1 week)..."
  sh "s3cmd sync --acl-public --exclude '*.*' --include  '*.css' --include '*.js' --add-header=\"Cache-Control: max-age=604800\"  public/ s3://jesseread.net"

  puts "\n--> Sync html files and sitemap (Cache: 2 hours)..."
  sh "s3cmd sync --acl-public --exclude '*.*' --include  '*.html' --include '*.xml' --add-header=\"Cache-Control: max-age=7200, must-revalidate\"  public/ s3://jesseread.net"

  puts "\n--> Syncing everything else"
  sh "s3cmd sync --acl-public --exclude '.DS_Store' public/ s3://jesseread.net"
end

desc "Deploy website to digital-ocean"
task :deploy do
  puts "Building site"
  system "jekyll build"
  puts "Syncing site to server"
  sh "rsync -avvzP public/ /var/www/blog"
end
