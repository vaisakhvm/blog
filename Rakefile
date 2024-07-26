desc "Create a new post"
task :post, [:title] do |t, args|
  title = args.title || "New Post"
  date = Time.now.strftime("%Y-%m-%d")
  filename = "_posts/#{date}-#{title.downcase.strip.gsub(' ', '-').gsub(/[^\w-]/, '')}.md"
  content = <<-EOF
---
layout: post
title: "#{title}"
date: #{date}
---
EOF
  File.open(filename, 'w') { |file| file.write(content) }
  puts "New post created: #{filename}"
end
