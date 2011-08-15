desc 'Build the manual'
task :man do
  require 'ronn'
  ENV['RONN_MANUAL']  = "aur-repo Manual"
  ENV['RONN_ORGANIZATION'] = "aur-repo v1.0.0"
  sh "ronn -w -s toc -r5 man/*.ronn"
end

desc 'Publish to github pages'
task :pages => :man do
  puts '----------------------------------------------'
  puts 'Rebuilding pages ...'
  verbose(false) {
    rm_rf 'pages'
    push_url = `git remote show origin`.scan(/Push.*URL.*/).first[/git@.*/]
    sh "
      set -e
      git fetch -q origin
      rev=$(git rev-parse origin/gh-pages)
      git clone -q -b gh-pages . pages
      cd pages
      git reset --hard $rev
      rm -f ronn*.html index.html
      cp -rp ../man/aur-repo.1.html ./index.html
      git add -u index.html
      git commit -m 'rebuild manual'
      git push #{push_url} gh-pages
       ", :verbose => false
  }
end

desc 'Install aur-repo and man pages'
task :install => :man do
  prefix = ENV['PREFIX'] || '/usr/local'

  man_dir = File.join(prefix, 'man', 'man1')
  bin_dir = File.join(prefix, 'bin')

  cp './aur-repo', bin_dir
  chmod 0755, File.join(bin_dir, 'aur-repo')
  cp './man/aur-repo.1', man_dir
end
