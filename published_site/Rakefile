require 'colorize'

desc "Commit _site/"
task :commit do
  puts "\n## Staging modified files"
  status = system("git add -A")
  puts status ? "Success".colorize(:green) : "Failed".colorize(:red)
  puts "\n## Committing a site build at #{Time.now.utc}"
  message = "Build site at #{Time.now.utc}"
  status = system("git commit -m \"#{message}\"")
  puts status ? "Success".colorize(:green) : "Failed".colorize(:red)
  puts "\n## Pushing commits to remote"
  status = system("git push origin source")
  puts status ? "Success".colorize(:green) : "Failed".colorize(:red)
end


desc "Deploy _site/ to master branch"
task :deploy do
  puts "\n## Deleting master branch"
  status = system("git branch -D master")
  puts status ? "Success".colorize(:green) : "Failed".colorize(:red)
  puts "\n## Creating new master branch and switching to it"
  status = system("git checkout -b master")
  puts status ? "Success".colorize(:green) : "Failed".colorize(:red)
  puts "\n## Forcing the published_site subdirectory to be project root"
  status = system("git filter-branch --subdirectory-filter published_site/ -f")
  puts status ? "Success".colorize(:green) : "Failed".colorize(:red)
  puts "\n## Switching back to source branch"
  status = system("git checkout source")
  puts status ? "Success".colorize(:green) : "Failed".colorize(:red)
  puts "\n## Pushing all branches to origin"
  status = system("git push --all origin --force")
  puts status ? "Success".colorize(:green) : "Failed".colorize(:red)
end

desc "Commit and deploy _site/"
  task :commit_deploy => [:commit, :deploy] do
end