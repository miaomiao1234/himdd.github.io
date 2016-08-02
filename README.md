[Jekyll](http://jekyllrb.com) 

1. 通过 安装 ruby

    ```
   ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
   brew install ruby
    ```

2. 通过 RubyGems 安装 Jekyll && bundle

    ```
    gem install jekyll
    gem install bundle
    # 可能需要添加国内 gems 源
    # 添加方法 https://ruby.taobao.org/
    ```

3. 执行：

    ```
    git clone https://github.com/himdd/himdd.github.io.git
    cd himdd.github.io
    bundle install
    ```

4. 预览效果，直接执行

    ```
    rake
    ```
    或者
    ```
    bundle exec jekyll serve
    ```

5. 如果是自己搭建的环境，修改完成后，执行

    ```
    rake build
    ```

6. 进行提交

    可以直接使用 ```git``` 提交：
    ```
    git push
    ```

    也可以使用
    ```
    rake deploy
    ```

    会自动提交给 gitlab，并且通过 webhook（需要seting ->Webhooks && Services配置） 回调部署机器
