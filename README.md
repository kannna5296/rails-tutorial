
# 手元で環境構築ログ

https://railsguides.jp/install_ruby_on_rails.html

## rbenvセットする
brew install rbenv ruby-build        
'eval "$(rbenv init -)"' >> ~/.bash_profile   >>> sourceする
rbenv rehash           
  

* rbenv 
  * https://qiita.com/Kodak_tmo/items/73147ed4f0eec54d6e94



## ruby install
rbenv local 3.4.2      global側使う意味はあんまりわかってない
* 切り替わらない時はwhich ruby... でrubyversionがどこ見てるか見る
  * https://qiita.com/akatsuki174/items/c0384b9903b4b5cbbdaf

## rails install
echo "gem: --no-document" >> ~/.gemrc　//
gem install rails
rails --version // Rails 8.0.1

https://railstutorial.jp/chapters/beginning?version=7.0#sec-installing_rails


* バージョン指定が微妙に効かなかった`gem install rails -v 7.0.4.3` こいつが出た⇩
```
/Users/my/.rbenv/versions/3.4.2/lib/ruby/gems/3.4.0/gems/activesupport-7.0.4.3/lib/active_support/logger_thread_safe_level.rb:12:in '<module:LoggerThreadSafeLevel>': uninitialized constant ActiveSupport::LoggerThreadSafeLevel::Logger (NameError)

    Logger::Severity.constants.each do |severity|
```

## bundle install
`rails _7.0.4.3_ new hello_app`しようとしたら上記activesupportうんたらで怒られた
GPTに聞くとbundle installがいるっぽい？
* Gemfile作った
```
source 'https://rubygems.org'

gem 'rails', '~> 7.1'
```
* bundle install
* 成功した


Ruby 3.4.2 を使っているなら、Rails 7.1 以上が必要

## new app
インストールしてる(利用できる)railsのどれかを指定しながらnew app
`rails _7.0.4.3_ new hello_app`→あかんっぽい（rubyVer3.4.2とあってないのかな）
`rails _7.2.2_ new hello_app`→OK,作れた


## Gemfileについて
https://railstutorial.jp/chapters/beginning?version=7.0#sec-bundler
* new appするとGemfileが新規にできる（rails newように作ったやつは不要なんかな）
* Gemfileは多分build.gradle的なやつ、ビルドに必要なライブラリを定義する場所
  * `>= 1.1.0` だと最新のジェムをとってくる
  * `~> 1.1.0` だとマイナーバージョンアップだけ取ってくる、メジャーバージョンアップはしない
  * `1.1.0 ` 数字だけの時は、有無を言わさず固定。


# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...
