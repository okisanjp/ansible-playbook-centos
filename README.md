### What is this?

vagrantで作ったCentOS6のVMを自動構成するために私が普段使っているplaybookから、基本的な部分を抽出したサンプルplaybookです

### 軽く説明

#### 実行

```
ansible-playbook vagrant.yml
```

vagrantのVMに接続するためのホスト名が`default`、接続に使う秘密鍵が`~/vm/.vagrant/machines/default/virtualbox/private_key`という前提で枳実されています。

環境ごとに書き換えて頂く必要がありますが、参考までに本環境での`vagrant ssh-config`実行結果を書いておきます

```
Host default
  HostName 127.0.0.1
  User vagrant
  Port 2222
  UserKnownHostsFile /dev/null
  StrictHostKeyChecking no
  PasswordAuthentication no
  IdentityFile /Users/okisanjp/vm/.vagrant/machines/default/virtualbox/private_key
  IdentitiesOnly yes
  LogLevel FATAL
```


### AnsibleのPipelining

`ansible.cfg`にてPipeliningをONにしている関係で、管理対象のOSで

#### /etc/sudoers.d/vagrant
```
Defaults:vagrant !requiretty
```

のような対応を行う必要があります

Pipeliningしない場合は上記設定は必要ありません。
