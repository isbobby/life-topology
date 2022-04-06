# Rakefile
Rake is a native tool for Ruby, similar to Unix's "make". It is used to handle administrative commands or tasks, which are stored either in a Rakefile or a .rake file.

Rake is a domain specific language, which means we can only use it for things related to Ruby. Rake allows one to write tasks in Ruby languages and execute them from the command line.

### Rake Dependencies
Rake uses dependencies as a computation method. Consider the following code

```
namespace :cucumber do
    Cucumber::Rake::Task.new({:ok => 'test:prepare'}, 'Run features that should pass') do |t|
      t.binary = vendored_cucumber_bin
      t.fork = true
      t.profile = 'default'
    end
	
[...]

desc 'Alias for cucumber:ok'
  task :cucumber => 'cucumber:ok'
  
task :default => :cucumber

task :features => :cucumber do
    STDERR.puts
end
```

The hash rockets `=>` represent *dependencies*, the first method won't run until the second has. 

### Example Rake Task
We can define a task in a Rakefile and execute the task in the command line.

```
task :play do
	puts "Here's a rake task!"
end

task :raking => [:play] do  
	puts "Should put this after :play"  
end
```

With this Rakefile, running `rake play` executes the play task. Running `rake raking` executes the `raking` task which depends on `play`



