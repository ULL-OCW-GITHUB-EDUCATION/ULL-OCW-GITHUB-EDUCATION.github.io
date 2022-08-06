desc "Publicar en GitHub los apuntes de OCW"
task :default do
  sh "git ci -am 'OCW 2022' && git push -u origin main"
end

desc "serve locally"
task :serve do
  sh "bundle exec jekyll serve --future --watch --drafts --host 0.0.0.0 --port 8084"
end

desc "stop the server"
task :stop do
  sh "ps aux |grep jekyll |awk '{print $2}' | xargs kill -9"
end

desc "build and watch locally"
task :bw do
  sh "bundle exec jekyll build --future --drafts --watch"
end

desc "build for the ocw course"
task :ocw do
  sh "bundle exec jekyll build -b '/ocw/pluginfile.php/19489/mod_resource/content/3/_site'"
end

task :updatebundler do
  sh "bundle update --bundler"
end

# docker run --rm --volume="$PWD:/srv/jekyll" --volume="$PWD/vendor/bundle:/usr/local/bundle" --env JEKYLL_ENV=development -p 4000:4000 jekyll/jekyll jekyll serve
# https://dev.to/michael/compile-a-jekyll-project-without-installing-jekyll-or-ruby-by-using-docker-4184
# docker run --rm 
# --volume="$PWD:/srv/jekyll" 
# --volume="$PWD/vendor/bundle:/usr/local/bundle" 
# --env JEKYLL_ENV=development -p 4000:4000 
# jekyll/jekyll:3.8 jekyll serve
task :docker do
  # sh 'docker run --rm --volume="$PWD:/srv/jekyll" --volume="$PWD/vendor/bundle:/usr/local/bundle" --env JEKYLL_ENV=development -p 4000:4000 jekyll/jekyll:3.8 jekyll serve'
  sh 'docker compose up' 
end
