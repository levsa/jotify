require 'rake/clean'

classes = 'classes'
target = 'target'
directory classes
directory target
jotify_jar = File.join(target, 'jotify.jar')

libs = FileList['lib/*.jar'].join(File::PATH_SEPARATOR)
src_files = FileList['src/**/*.java']

CLEAN.include(classes, target)

task :compile => classes do
 src_files = FileList['src/**/*.java']
 sh "javac", '-target', '1.6', '-d', classes, '-classpath', libs, *src_files
end

desc "run jotify"
task :run => :compile do
 sh "java -classpath src:#{classes}:#{libs} de.felixbruns.jotify.gui.JotifyApplication"
end

desc "creates #{jotify_jar}"
task :jar => [:compile, target] do
  sh "jar cf #{jotify_jar} -C classes ."
end

desc "runs the gateway application"
task :gateway => [:compile] do
  sh "java -classpath src:#{classes}:#{libs} de.felixbruns.jotify.gateway.GatewayApplication"
end
