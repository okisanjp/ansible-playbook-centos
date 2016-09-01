### AnsibleのPipelining

`ansible.cfg`にてPipeliningをONにしている関係で、管理対象のOSで

#### /etc/sudoers.d/vagrant
```
Defaults:vagrant !requiretty
```

のような対応を行う必要があります

Pipeliningしない場合は上記設定は必要ありません。
