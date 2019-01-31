---
layout: page
title: 使用 Jekyll 製作 Github Pages
---
> 紀錄最近使用 Jekyll 來製作個人網頁的心得。

# 1. 環境安裝與簡介
使用 MacOS 10.13.3 並且參考官方網站上的安裝流程 [Jekyll Installation][jekyll guide]。

Jekyll 是 [Ruby][Ruby] 的套件，使用 [RubyGem][RubyGem] 來安裝管理，也可以用 [Bundler][Bundler] 來維護不同專案之間使用不同的 Gems 以及版本可能發生的衝突。 作為 static site generator ，Jekyll 非常簡潔並且適合於 blog，甚至連 Github Pages 都免費支援！(參考 [Link][Github Jekyll])

首先可以根據 [Ruby Installation][Ruby Installation] 來安裝 Ruby ，並使用 RVM 等等程式來管理 Ruby 的版本，Mac OS X 使用者可以參考這篇[文章][Install RVM]。

- 安裝 Jekyll 和 Bundler
```shell
$ gem install jekyll bundler
```

- 確認安裝版本
```shell
$ jekyll -v
```

[jekyll guide]: https://jekyllrb.com/docs/installation/
[RubyGem]: https://rubygems.org/
[Bundler]: http://bundler.io/
[Ruby]: https://www.ruby-lang.org/zh_tw/
[Ruby Installation]: https://www.ruby-lang.org/zh_tw/documentation/installation/
[Install RVM]: http://usabilityetc.com/articles/ruby-on-mac-os-x-with-rvm/
[Github Jekyll]: https://help.github.com/articles/using-jekyll-as-a-static-site-generator-with-github-pages/

# 2. 建立新的 blog
- Jekyll 內建指令來幫助使用者建立新的 blog
```shell
$ jekyll new my_blog
$ cd my_blog
```
第一行指令會建立一個新的資料夾在當前目錄，因為要將 blog 放到 Github 上面，根據 Github 個人頁面的規定，建議命名為 `<username>.github.io`。
- 為了讓 blog 可以正確顯示在 Github Pages 上面，確認檔案 Gemfile 中是否有加入以下兩行
```
source 'https://rubygems.org'
gem 'github-pages', group: :jekyll_plugins
```
完成後將 my\_blog 這個 respository push 到 Github 上面，在 Setting 頁面中確認個人網站的 URL 以及所使用的 branch 是否正確即可。(關於 Gemfile 的詳細語法可以參考官方 [Docs][Bundle Gemfile])
- 如果以上的設置正確，並且至 Github 上面確認檔案放置正確（可參考 [Link][My github.io]），經過數分鐘後連至 https://\<username\>.github.io 應該可以看到模板 blog，到這裡已經完成個人頁面的架設了！

[Bundle Gemfile]: http://bundler.io/v1.5/gemfile.html
[My github.io]: https://github.com/yen-shi/yen-shi.github.io

# 3. 簡單設定 Jekyll
- 在 my\_blog 資料夾底下使用以下指令可以在 local 端產生並在 `http://localhost:4000/` 預覽
```shell
bundle exec jekyll serve --watch --livereload --incremental
```
`--watch` 會觀察本地端檔案是否有改變並重新產生新的檔案。  
`--livereload` 使我們瀏覽的時候不需要重整頁面。  
`--incremental` 讓每次 build 的時候只會針對修改部分。  
- Jekyll 所做的事情是將檔案根據當前目錄的配置進行處理後將結果存放在 `_site` 目錄底下
<img src="/images/jekyll-files.png" alt="Jekyll original files">
- 可以預覽網站後第一件事情是發現排版不是很好看...  
在 Jekyll 裡面，我們可以使用不同的 Theme 來做版面的配置，預設的 Theme 是 `minima`，它的版面配置檔案路徑可以使用 `bundle show minima` 來檢視，
<img src="/images/theme-minima.png" alt="Tree of minima">
跟據[官網][官網]的文件，如果要對 Theme 做修改，只要在 my\_blog 資料夾中建立相同路徑的檔案就可以覆蓋掉 default 的參數，`_layouts`資料夾定義了頁面的排列，`_sass`則是定義了頁面的樣貌，在 Jekyll 裡面可以使用 SCSS 語法來撰寫 CSS，參考這篇[文章][文章]可以對 SCSS 有初步的了解，這樣一來就可以對自己的 Blog 進行任意的調整了！

[官網]: https://jekyllrb.com/docs/themes/
[文章]: http://eddychang.me/blog/others/91-scss-15-mins.html