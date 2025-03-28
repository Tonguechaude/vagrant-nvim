$script_jammy = <<-SCRIPT
if [ ! -f /opt/puppetlabs/bin/puppet ]; then
  sudo wget --quiet https://apt.puppetlabs.com/puppet7-release-jammy.deb
  sudo dpkg -i puppet7-release-jammy.deb
  sudo apt-get update
  sudo apt-get install puppet-agent
  sudo apt-get update
fi
SCRIPT

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/jammy64"
  config.vm.provider "virtualbox" do |vb|
    vb.name = "nvim"
  end
  
  config.vm.provision "shell", inline: $script_jammy
  config.vm.provision "puppet" do |puppet|
    puppet.working_directory = "/tmp/vagrant-puppet"
    puppet.module_path = "modules"
    puppet.manifest_file = "default.pp"
  end
end