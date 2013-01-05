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
    idp_config.vm.share_folder "templatedir", "/var/lib/puppet/templates",      "puppet/templates"
    idp_config.vm.share_folder "moduledir",   "/etc/puppet/modules",            "puppet/modules"
    idp_config.vm.share_folder "manifestdir", "/etc/puppet/manifests",          "puppet/manifests"
  end

  config.vm.define :sp do |sp|
    sp.vm.box = "centos62_v2"
    sp.vm.box_url = "http://dl.dropbox.com/u/64693533/vagrant/centos62-v2.box"
    sp.vm.host_name = "sp.training.shib"
    sp.vm.network :hostonly, "192.168.6.111"
    #sp.vm.boot_mode = :gui
    sp.vm.provision :puppet do |puppet|
      puppet.manifest_file  = "site.pp"
      puppet.manifests_path = "puppet/manifests"
      puppet.module_path    = "puppet/modules"
    end
    sp.vm.share_folder "templatedir", "/var/lib/puppet/templates",  "puppet/templates"
    sp.vm.share_folder "moduledir",   "/etc/puppet/modules",        "puppet/modules"
    sp.vm.share_folder "manifestdir", "/etc/puppet/manifests",      "puppet/manifests"
  end

end
