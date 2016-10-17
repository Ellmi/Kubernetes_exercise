Vagrant.configure("2") do |config|

  cluster = {
      "k8s-master-1" => {:ip => "10.8.29.2", :cups => 2, :memory => 4096},
      "k8s-slave-1" => {:ip => "10.8.29.3", :cups => 1, :memory => 2048},
      "k8s-slave-2" => {:ip => "10.8.29.4", :cups => 1, :memory => 2048}
  }

  config.vm.box = "ubuntu/trusty64"
  config.vm.box_check_update = false

  cluster.each_with_index do |(hostname, info), index|

    config.vm.define hostname do |cfg|

      cfg.vm.hostname = hostname
      cfg.vm.network :private_network, ip: "#{info[:ip]}"

      config.vm.provider "virtualbox" do |vb|

        vb.name = "#{hostname}"
        vb.cpus = info[:cups]
        vb.memory = info[:memory]

      end
    end
  end
end
