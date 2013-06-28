CSS_FILES = FileList['css/*.css']
LAYOUT_FILES = FileList['_layouts/**']
SOURCE_FILES = FileList['*.textile']
SITE_FILES = SOURCE_FILES.gsub(/(.*)\.textile/, '_site/\1.html')

task :jekyll => SOURCE_FILES + CSS_FILES + LAYOUT_FILES do
  sh "jekyll build"
end

SITE_FILES.each do |f|
  file f => :jekyll
end

# TODO: use SITE_FILES instead
["resume", "one-sheet"].each do |name|
  file "#{name}.pdf" => ["_site/#{name}.html"] do |t|
    sh "prince --verbose -s _site/css/resume-prince.css _site/#{name}.html -o #{t.name}"
  end

  task :default => ["#{name}.pdf"]
end
