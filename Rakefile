require 'rubygems'
require 'rake'

begin
  require 'jeweler'
  Jeweler::Tasks.new do |gem|
    gem.name = "br-cpf"
    gem.summary = %Q{Calculates and validates given CPF}
    gem.description = %Q{Lib implemented in C that calculates and validates CPF.}
    gem.email = "bbcoimbra@gmail.com"
    gem.homepage = "http://github.com/bbcoimbra/br-cpf"
    gem.authors = ["Bruno Coimbra"]
    gem.add_development_dependency "rspec", ">= 1.2.9"
    gem.files = FileList["lib/**/*.rb", "ext/**/*"]
    gem.files.exclude 'lib/*.so'
    gem.extensions = FileList["ext/**/extconf.rb"]
    # gem is a Gem::Specification... see http://www.rubygems.org/read/chapter/20 for additional settings
  end
  Jeweler::GemcutterTasks.new
rescue LoadError
  puts "Jeweler (or a dependency) not available. Install it with: gem install jeweler"
end

require 'rake/extensiontask'
Rake::ExtensionTask.new('CPF')
CLEAN.include('lib/**/*.so')

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

task :default => :spec

require 'rake/rdoctask'
Rake::RDocTask.new do |rdoc|
  version = File.exist?('VERSION') ? File.read('VERSION') : ""

  rdoc.rdoc_dir = 'rdoc'
  rdoc.title = "br-cpf #{version}"
  rdoc.rdoc_files.include('README*')
  rdoc.rdoc_files.include('lib/**/*.rb')
end

