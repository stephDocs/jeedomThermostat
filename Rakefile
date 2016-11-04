require 'rubygems'
require 'tmpdir'
require 'bundler/setup'








# Indiquez le nom de votre dépôt
GITHUB_REPONAME = "stephDocs/jeedomThermostat"

namespace :site do


  desc "Génération et publication des fichiers sur GitHub"
  task :publish  do
   
     
  
 
    cp_r "doc/images/.", "_site/images"

    Dir.mktmpdir do |tmp|
      cp_r "_site/.", tmp
      
      pwd = Dir.pwd
      Dir.chdir tmp
      File.open(".nojekyll", "wb") { |f| f.puts("Site généré localement.") }
      
      system "git init"
      system "git add ."
      message = "Site mis à jour le #{Time.now.utc}"
      system "git commit -m #{message.inspect}"
      system "git remote add origin git@github.com:#{GITHUB_REPONAME}.git"
      system "git push origin master:refs/heads/gh-pages --force"

      Dir.chdir pwd
    end
  end
end
