Vagrant.configure("2") do |config|
  config.vm.define "rancher" do |web|
      web.vm.box = "ubuntu/focal64"
      web.vm.box_download_insecure = true
      web.vm.network "public_network", bridge: "Realtek Gaming GbE Family Controller", ip: "192.168.0.120"
      web.vm.provision "shell", path: "script.sh"
      config.vm.provider "virtualbox" do |v|
        v.memory = 2048
        v.cpus = 4
      end
  end

  (1..3).each do |i|
      config.vm.define "k8s-#{i}" do |kubs|
          kubs.vm.box = "ubuntu/focal64"
          kubs.vm.box_download_insecure = true
          kubs.vm.network "public_network", bridge: "Realtek Gaming GbE Family Controller", ip: "192.168.0.12#{i}"
          kubs.vm.provision "shell", path: "script.sh"
          config.vm.provider "virtualbox" do |v|
            v.memory = 2048
            v.cpus = 4
          end
      end
  end
end
