Vagrant::Config.run do |config|

  config.vm.define :idp do |idp_config|
    idp_config.vm.box = "centos62_v2"
    idp_config.vm.box_url = "http://dl.dropbox.com/u/64693533/vagrant/centos62-v2.box"
    idp_config.vm.network :hostonly, "192.168.6.110"
    idp_config.vm.host_name = "idp.training.shib"
    #idp_config.vm.boot_mode = :gui
    idp_config.vm.provision :puppet do |puppet|
      puppet.manifests_path = "puppet/manifests"
      puppet.manifest_file  = "site.pp"
      puppet.module_path    = "puppet/modules"
    end
    idp_config.vm.forward_port 8443, 8443
    idp_config.vm.share_folder "templatedir", "/var/lib/puppet/templates",      "puppet/templates"
    idp_config.vm.share_folder "moduledir",   "/etc/puppet/modules",            "puppet/modules"
    idp_config.vm.share_folder "manifestdir", "/etc/puppet/manifests",          "puppet/manifests"
  end

  config.vm.define :app do |app_config|
    app_config.vm.box = "centos62_v2"
    app_config.vm.box_url = "http://dl.dropbox.com/u/64693533/vagrant/centos62-v2.box"
    app_config.vm.host_name = "app.training.shib"
    app_config.vm.network :hostonly, "192.168.6.111"
    #app_config.vm.boot_mode = :gui
    app_config.vm.provision :puppet do |puppet|
      puppet.manifest_file  = "site.pp"
      puppet.manifests_path = "puppet/manifests"
      puppet.module_path    = "puppet/modules"
    end
    app_config.vm.forward_port 6443, 6443
    app_config.vm.share_folder "templatedir", "/var/lib/puppet/templates",  "puppet/templates"
    app_config.vm.share_folder "moduledir",   "/etc/puppet/modules",        "puppet/modules"
    app_config.vm.share_folder "manifestdir", "/etc/puppet/manifests",      "puppet/manifests"
  end

end
