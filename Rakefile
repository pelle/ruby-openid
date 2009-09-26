require 'rubygems'
require 'rake'

begin
  require 'jeweler'
  Jeweler::Tasks.new do |gem|
    gem.name = 'ruby-openid'
    gem.author = 'JanRain, Inc'
    gem.email = 'openid@janrain.com'
    gem.homepage = 'http://openidenabled.com/ruby-openid/'
    gem.summary = 'A library for consuming and serving OpenID identities.'
    gem.extra_rdoc_files = ["LICENSE", "README", "INSTALL","UPGRADE","CHANGELOG", "CHANGES-2.1.0", "UPGRADE"]
    gem.files.exclude "admin","_darcs","coverage",".gitignore","gemspec"
  end
rescue LoadError
  puts "Jeweler (or a dependency) not available. Install it with: sudo gem install jeweler"
end

require 'rake/testtask'
Rake::TestTask.new(:test) do |test|
  test.libs << 'lib' << 'test'
  test.ruby_opts = ['-rtestutil']
  test.pattern = 'test/**/test_*.rb'
  test.verbose = true
end

begin
  require 'rcov/rcovtask'
  Rcov::RcovTask.new do |test|
    test.libs << 'test'
    test.ruby_opts = ['-rtestutil']
    test.pattern = 'test/**/test_*.rb'
    test.verbose = true
  end
rescue LoadError
  task :rcov do
    abort "RCov is not available. In order to run rcov, you must: sudo gem install spicycode-rcov"
  end
end

task :test => :check_dependencies

task :default => :test

require 'rake/rdoctask'
Rake::RDocTask.new do |rdoc|
  if File.exist?('VERSION')
    version = File.read('VERSION')
  else
    version = ""
  end

  rdoc.rdoc_dir = 'rdoc'
  rdoc.title = "ruby-openid #{version}"
  rdoc.rdoc_files.include('README*')
  rdoc.rdoc_files.include('lib/**/*.rb')
end
