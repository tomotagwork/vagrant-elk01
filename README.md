# vagrant-elk01
Virtual Box 上に ELK/Ubuntu環境を構築するためのVagrantファイルです。
ansible_localを使ってパッケージのインストール等を行っています。
VagrantもAnsibleも初心者なもので色々不作法がありそうですが、ご了承ください。

OpenJDK9, Elasticsearch, Kibana, Logstashを導入しています。
Elasticsearch, Kiabanaはそれぞれ任意のIPでListenするよう構成追加しているのみで、他はデフォルトのままです。
Elasticsearch, Kibanaは自動起動するようにしています。
デフォルト構成なのでゲストOS上はElasticsearchは9200,Kibanaは5601ポートでListenするようになっていますが、ホストOS側にはそれぞれ19200, 15601ポートで公開しています。
そのため、ホストOSからは、localhost:19200, localhost:15601 でアクセス可能です。

Vagrantfileと同じディレクトリにelasticsearchというディレクトリを用意しておく必要があります。(dummy.txtファイルが置いてあります)
これは、ゲストOSのElasticsearchがデータを保持するディレクトリ /var/lib/elasticsearch からこのディレクトリ(/vagrant/elasticsearch)にシンボリックリンクを張っているためです。
Elasticsearchにデータを突っ込んでいく際に、ゲストOS側のファイルシステムが使われるのを回避するために、このようにホストOS側にリダイレクトするようにしています。

# 使い方
ファイル一式を同一ディレクトリに配置して、そのディレクトリからvagrant upを実行
あとは普通にvagrantコマンドで操作

|操作 | コマンド  |
|:--|:---|
|起動|vagrant up|
|SSH接続|vagrant ssh|
|停止|vagrant halt|
|Vagrantファイル更新反映 | vagrant reload|
|VM破棄 | vagrant destroy|

