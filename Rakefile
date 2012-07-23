require "stringex"


source_dir = '_src/'
post_dir = '_src/_posts/'
filetype = 'markdown'


task :default do
    puts "Blub"
end

desc "Create a new page"
task :new_post, :title do |t, args|
    args.with_defaults(:title => 'new-post')
    title = args.title

    filename = "#{post_dir}#{Time.now.strftime('%Y-%m-%d')}-#{title.to_url}.#{filetype}"
    if File.exists?(filename)
        abort("rake aborted!") if ask("#{filename} already exists. Do you want to overwrite?", ['y','n']) == 'n'
    end

    puts "Creating new post: #{filename}"
    open(filename, 'w') do |post|
        post.puts "---"
        post.puts "layout: post"
        post.puts "title: \"#{title.gsub(/&/,'&amp;')}\""
        post.puts "categories:"
        post.puts "tags:"
        post.puts "published: false"
        post.puts "---"
    end
end
