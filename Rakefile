require 'rubygems'
require 'rake'

begin
  require 'jeweler'
  Jeweler::Tasks.new do |gem|
    gem.name = "postmark"
    gem.summary = %Q{Ruby gem for sending emails through http://postmarkapp.com HTTP API}
    gem.description = %Q{Ruby gem for sending emails through http://postmarkapp.com HTTP API. It relieas on TMail::Mail for message construction.}
    gem.email = "underlog@gmail.com"
    gem.homepage = "http://postmarkapp.com"
    gem.authors = ["Petyo Ivanov", "Ilya Sabanin"]
    gem.add_development_dependency "rspec"
    gem.add_development_dependency "cucumber"
    gem.add_dependency "tmail"
    gem.files << "lib/postmark/tmail_mail_extension.rb"
    gem.post_install_message = %q[
      ==================
      Thanks for installing the postmark gem. If you don't have an account, please sign up at http://postmarkapp.com/.
      Review the README.rdoc for implementation details and examples.
      ==================
    ]
    # gem is a Gem::Specification... see http://www.rubygems.org/read/chapter/20 for additional settings
  end
  Jeweler::GemcutterTasks.new
rescue LoadError
  puts "Jeweler (or a dependency) not available. Install it with: sudo gem install jeweler"
end

require 'spec/rake/spectask'
Spec::Rake::SpecTask.new(:spec) do |spec|
  spec.libs << 'lib' << 'spec'
  spec.spec_files = FileList['spec/**/*_spec.rb']
end

Spec::Rake::SpecTask.new(:rcov) do |spec|
  spec.libs << 'lib' << 'spec'
  spec.pattern = 'spec/**/*_spec.rb'
  spec.rcov = true
end

task :spec => :check_dependencies

begin
  require 'cucumber/rake/task'
  Cucumber::Rake::Task.new(:features)

  task :features => :check_dependencies
rescue LoadError
  task :features do
    abort "Cucumber is not available. In order to run features, you must: sudo gem install cucumber"
  end
end

task :default => :spec

require 'rake/rdoctask'
Rake::RDocTask.new do |rdoc|
  if File.exist?('VERSION')
    version = File.read('VERSION')
  else
    version = ""
  end

  rdoc.rdoc_dir = 'rdoc'
  rdoc.title = "postmark #{version}"
  rdoc.rdoc_files.include('README*')
  rdoc.rdoc_files.include('lib/**/*.rb')
end
