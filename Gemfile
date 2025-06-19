# Gemfile 最顶部添加
ruby '3.1.7'  # 明确 Ruby 版本
source "https://mirrors.aliyun.com/rubygems"

# 锁定 Bundler 版本与 CI 环境一致
gem 'bundler', '2.4.22'

# 剩余内容保持不变
gem "github-pages", "~> 227", group: :jekyll_plugins
# 如果需要额外插件，放在这里
group :jekyll_plugins do
  gem "jekyll-feed", "~> 0.12"
end

# Windows 和 JRuby 的时区支持
platforms :mingw, :x64_mingw, :mswin, :jruby do
  gem "tzinfo", ">= 1", "< 3"
  gem "tzinfo-data"
end

# Windows 文件监听性能优化
gem "wdm", "~> 0.1", :platforms => [:mingw, :x64_mingw, :mswin]

# JRuby 的 http_parser.rb 锁定版本
gem "http_parser.rb", "~> 0.6.0", :platforms => [:jruby]