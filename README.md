
我的blog [http://himdd.github.io](http://himdd.github.io) 
1. 如果本机版本过低，可通过brew 安装 ruby，否则跳过

    ```
    #安装brew
    ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
    #安装ruby
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


5. 进行提交

    可以直接使用 ```git``` 提交：
    ```
    git push
    ```

5. 如果是自己搭建的环境，修改完成后，执行

    ```
    rake build
    ```

    提交也可以使用
    ```
    rake deploy
    ```
    会自动提交给 github，并且通过 webhook（需要seting ->Webhooks && Services配置） 回调部署机器
6.更多
[Jekyll](http://jekyllrb.com) 
