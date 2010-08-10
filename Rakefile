CSS_FILES = FileList['css/*.css']
LAYOUT_FILES = FileList['_layouts/**']
SITE_FILES = FileList['_site/**']

file '_site/resume.html' => ['resume.textile'] + CSS_FILES + LAYOUT_FILES do |t|
  sh "jekyll --pygments --safe"
end

file 'resume.pdf' => SITE_FILES do |t|
  sh "prince --verbose -s _site/css/resume-prince.css _site/resume.html -o #{t.name}"
end

task :default => ['resume.pdf']
