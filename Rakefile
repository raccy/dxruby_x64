# frozen_string_literal: true

require 'rake/clean'

CLEAN.include('src/*.o', 'src/Makefile', 'src/dxruby-x64-mingw32.def',
              'src/dxruby.so')
CLOBBER.include('src')

DXRUBY_VERSION = '1.4.5'
DXRUBY_SVNROOT = 'https://svn.osdn.net/svnroot/dxruby/'
DXRUBY_SVN_URL = "#{DXRUBY_SVNROOT}tags/#{DXRUBY_VERSION}/"

directory 'src' do
  sh "svn co #{DXRUBY_SVN_URL} src"
end

desc 'checkout'
task checkout: 'src'

desc 'revert'
task revert: :checkout do
  Dir.chdir('src') do
    sh 'svn revert -R .'
    rm 'patched' if FileTest.exist?('patched')
  end
end

file_create 'src/patched' => :checkout do
  sh 'patch --binary -p 0 < dxruby_x64.patch'
  touch 'src/patched'
end

desc 'patch'
task patch: 'src/patched'

file_create 'src/Makefile' => :patch do
  Dir.chdir('src') do
    sh 'ruby extconf.rb'
  end
end

desc 'configure'
task config: 'src/Makefile'

file_create 'src/dxruby.so' => :config do
  Dir.chdir('src') do
    sh 'make'
  end
end

desc 'build (defualt)'
task build: 'src/dxruby.so'

desc 'install'
task install: [:build, :config] do
  Dir.chdir('src') do
    sh 'make install'
  end
end

task default: :build
