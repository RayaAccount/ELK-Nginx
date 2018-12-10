FROM docker.elastic.co/elasticsearch/elasticsearch:6.2.3

COPY ./conf/elasticsearch.yml /usr/share/elasticsearch/config/elasticsearch.yml

# kuromojiをインストール
RUN elasticsearch-plugin  install analysis-kuromoji

# RUN elasticsearch-plugin remove x-pack
