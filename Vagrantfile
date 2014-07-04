# -*- mode: ruby -*-
# vi: set ft=ruby :

# require plugin for testing via bundler
Vagrant.require_plugin "vagrant-toplevel-cookbooks"
Vagrant.require_plugin "vagrant-omnibus"
Vagrant.require_plugin "vagrant-cachier"

Vagrant.configure("2") do |config|

  config.omnibus.chef_version = "11.6.0"
  config.cache.auto_detect = true

  config.vm.box = "opscode_ubuntu-12.04_provisionerless"
  config.vm.box_url = "https://opscode-vm-bento.s3.amazonaws.com/vagrant/opscode_ubuntu-12.04_provisionerless.box"

  #
  # configure vm to be deployed with toplevel cookbook
  #
  config.vm.define :my_app do |my_app_config|
    # app cookbook to deploy
    my_app_config.toplevel_cookbook.url = "https://github.com/tknerr/sample-toplevel-cookbook"

    my_app_config.vm.provision :chef_solo do |chef|
      chef.add_recipe "sample-app"
      chef.json = {
        :sample_app => {
          :words_of_wisdom => "Chuck Norris' beard can type 140 wpm!"
        }
      }
    end
  end

  #
  # example for deploying a specific branch
  #
  config.vm.define :my_app_branched do |my_app_config|
    # app cookbook to deploy
    my_app_config.toplevel_cookbook.url = "https://github.com/tknerr/sample-toplevel-cookbook"
    my_app_config.toplevel_cookbook.ref = "lxc"

    my_app_config.vm.provision :chef_solo do |chef|
      chef.add_recipe "sample-app"
    end
  end

  #
  # example using a local file url
  #
  config.vm.define :my_app_local_file do |my_app_config|
    # app cookbook to deploy
    my_app_config.toplevel_cookbook.url = "file://D:/Repos/_github/_cookbooks/sample-toplevel-cookbook"
    
    my_app_config.vm.provision :chef_solo do |chef|
      chef.add_recipe "sample-app"
    end
  end

  #
  # example without toplevel cookbook configured
  #
  config.vm.define :my_app_no_toplevel_cookbook do |my_app_config|
    my_app_config.vm.provision :chef_solo do |chef|
      chef.add_recipe "sample-app"
    end
  end

  #
  # example without provisioner - should kick in here
  #
  config.vm.define :my_app_no_provisioner do |my_app_config|
    # app cookbook to deploy
    my_app_config.toplevel_cookbook.url = "https://github.com/tknerr/sample-toplevel-cookbook"
  end

end
