#!/usr/bin/env rake

require 'rails'
# require "activeadmin"
require "rspec/core/rake_task"

desc "Creates a test rails app for the specs to run against"
task :setup do
  require 'rails/version'
  system("mkdir spec/rails") unless File.exist?("spec/rails")
  system "bundle exec rails new --skip-bootsnap --skip-active-storage --skip-active-job --skip-action-cable --skip-asset-pipeline spec/rails/rails-#{Rails::VERSION::STRING} -m spec/support/rails_template_with_data.rb"
end

RSpec::Core::RakeTask.new
task :default => :spec
task :test => :spec

desc "build the gem"
task :build do
  system "gem build activeadmin-axlsx.gemspec"
end
desc "build and release the gem"
task :release => :build do
  system "gem push activeadmin-axlsx-#{ActiveAdmin::Axlsx::VERSION}.gem"
end
