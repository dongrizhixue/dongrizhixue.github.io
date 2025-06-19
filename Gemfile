source "https://mirrors.aliyun.com/rubygems"

# 使用 github-pages 统一管理依赖（已包含 jekyll、minima 等）
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