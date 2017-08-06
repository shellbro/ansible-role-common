Vagrant.configure("2") do |config|
  config.vbguest.auto_update = false
  
  config.vm.define "centos" do |centos|
    centos.vm.box = "centos/7"
  end

  config.vm.define "fedora" do |fedora|
    fedora.vm.box = "fedora/25-cloud-base"
    fedora.vm.provision "shell" do |s|
      s.inline = "dnf -y install python python2-dnf libselinux-python"
    end
    fedora.vm.provision "ansible" do |a|
      a.limit = "all"
      a.playbook = "tests/test-vagrant.yml"
    end
  end
end
