Vagrant.configure("2") do |config|
  if Vagrant.has_plugin?("vagrant-cachier")
    config.cache.scope = :box
  end

  config.vm.define "v2-mirror" do |m|
    m.vm.box = "debian/jessie64"

    m.vm.network :forwarded_port, host: 8080, guest: 80
    m.vm.network :forwarded_port, host: 5000, guest: 5000

    m.vm.synced_folder "data/", "/data", mount_options: ['dmode=777','fmode=755']

    m.vm.provision "docker"
    m.vm.provision "docker_compose",
      yml: "/vagrant/docker-compose.yml",
      compose_version: "1.6.2"
    m.vm.provision "ansible" do |ansible|
      ansible.playbook = "playbook.yml"
    end
  end
end
