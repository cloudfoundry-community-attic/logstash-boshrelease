Vagrant::Config.run do |config|
  config.vm.box = "bosh-solo-0.6.4"
  downloads = "https://github.com/downloads/drnic/bosh-solo/"
  config.vm.box_url = "#{downloads}bosh-solo-0.6.4.box"

  config.vm.forward_port 9292, 9292 # logstash
  config.vm.forward_port 9200, 9200 # elasticsearch
  config.vm.forward_port 5601, 5601 # Kibana
  config.vm.forward_port 3000, 3000 # some rails app
  config.vm.forward_port 6380, 6380 # Redis (non-traditional port)

  config.vm.provision :shell, :path => "scripts/vagrant-setup.sh"

  if local_bosh_src = ENV['BOSH_SRC']
    config.vm.share_folder "bosh-src", "/bosh", local_bosh_src
  end
end
