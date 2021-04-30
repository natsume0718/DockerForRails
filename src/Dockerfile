# マルチステージビルドでNode入れる
FROM node:14-alpine as node

FROM ruby:2.7

# nodeとyarnコピー
COPY --from=node /opt/yarn-* /opt/yarn
# シンボリックリンクはる
RUN ln -fs /opt/yarn/bin/yarn /usr/local/bin/yarn

RUN apt-get update && \
    apt-get install -y git vim less build-essential graphviz cron bash g++ nodejs && \
    apt-get clean

#Railsアプリのルートディレクトリ作成
ENV RAILS_ROOT /var/www/src
RUN mkdir -p $RAILS_ROOT

WORKDIR $RAILS_ROOT

RUN mkdir -p $RAILS_ROOT/tmp/sockets

RUN node -v && yarn -v

# ホストのGemfileのコピー
COPY Gemfile Gemfile
COPY Gemfile.lock Gemfile.lock

RUN gem install puma
RUN bundle install --jobs 20 --retry 5 --without production