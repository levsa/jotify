require 'rake/clean'

classes = 'classes'
directory classes

libs = FileList['lib/*.jar'].join(File::PATH_SEPARATOR)
src_files = FileList['src/**/*.java']

CLEAN.include(classes)

task :compile => classes do
 src_files = FileList['src/**/*.java']
 sh "javac", '-d', classes, '-classpath', libs, *src_files
end

task :run => :compile do
 sh "java -classpath src:#{classes}:#{libs} de.felixbruns.jotify.gui.JotifyApplication"
end
