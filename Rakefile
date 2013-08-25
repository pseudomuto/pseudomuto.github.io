
desc "starts a simple http server on port 8000"
task :server do
  system "jekyll serve"
end

desc "compiles the site"
task :generate do
  system "jekyll build"
end

namespace :generate do
  desc "generate a new post"
  task :post, :title do |task, args|
    date_parts = Time.now.localtime.to_s.split
    puts date_parts.to_s

    template = <<TEMPLATE
---
layout: post
title:  "#{args[:title]}"
date:   #{date_parts.join(' ')}
categories: development
---
TEMPLATE

    file_name = "_posts/#{date_parts[0]}-#{args[:title]}.md"
    File.write(file_name, template)
    puts "generated #{file_name}"
  end
end

task :default => :server