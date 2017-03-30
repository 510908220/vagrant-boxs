# vagrant-boxs
整理vagrant box, 并放在百度云上.

## Boxs



| 名称                                       | 下载地址                                     | 百度云                              | 描述                         |
| ---------------------------------------- | ---------------------------------------- | -------------------------------- | -------------------------- |
| ubuntu/trusty64                          | https://atlas.hashicorp.com/ubuntu/boxes/trusty64 | https://pan.baidu.com/s/1jHQ1ceM |                            |
| ubuntu/xenial64                          | https://atlas.hashicorp.com/ubuntu/boxes/xenial64 | https://pan.baidu.com/s/1i55eDxF |                            |
| Ubuntu 14.04 with Docker enabled (based on amd64 server iso file) | https://github.com/jose-lpa/packer-ubuntu_lts/releases/download/v2.0/ubuntu-14.04.box | https://pan.baidu.com/s/1bp5qRQf | 含有docker                   |
| ubuntu-14.04-aliyun-docker.box           |                                          |                                  | 加入了阿里云的ubuntu源和阿里云docker加速 |

*要是百度云链接失效的话,联系qq:510908220*


## Vagrantfile
> 下面是一个`Vagrantfile`的例子:

```v
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu-14.04.box"
  config.vm.hostname = "westdoorblowcola"
  config.vm.network :private_network, ip: "192.168.0.66"
  config.vm.synced_folder "F:/studio/boxs/shared", "/vagrant_data",id: "vagrant-root",
      owner: "vagrant",
      group: "www-data",
      mount_options: ["dmode=775,fmode=764"]
  config.vm.provider :virtualbox do |vb|
    vb.customize [
      "modifyvm", :id,
      "--natdnshostresolver1", "on",
      "--memory", "1024"
    ]
  end
end
```

