# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.provision "shell", inline: <<-SHELL
    echo "127.0.0.1 localhost
192.168.99.10 docker.salas4linux.com.br
192.168.99.11 devops.salas4linux.com.br
192.168.99.12 automation.salas4linux.com.br" > /etc/hosts 
    mkdir /root/.ssh/
    #Private
    echo "-----BEGIN RSA PRIVATE KEY-----
-----END RSA PRIVATE KEY-----" >> /root/.ssh/id_rsa
    #Public
    echo "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQD6JzMKd01aHEPVi0LGSTxSiDZUiOVVx9RkweBbQgFUq6q4Q3/p8jri+YH4e1c9IZWExaTF9IFVl2ve8lu6LtZaVqxJA++gst+ory1aW5tGJipQLC6uwg80Dpw3bZbdtE7R5wICtsfm56x6HdXgLjscbgv+bLGpC7Ff+fxZCtqPT7W9tumOLANAST/Eh+1y7JgrSbAcvUcbWxI/2//3KXVxw0in1fPs6litPxR8iUfvUukS7/wGPF7qgixYz21uTINI/L371MPF3K43jtuCEneWolh+c4/Qw2FjscBOhWfG+YhDfRciNKGPkKIuI3txuj6xFInwqhkciOLXMp4XYRyL" >> /root/.ssh/authorized_keys
    chmod 600 /root/.ssh/id_rsa
  SHELL

#DOCKER
  config.vm.define "docker" do |docker| 				     # configurar a definição de vm chamada docker
    docker.vm.hostname = "docker"        				     # hostname da maquina
    docker.vm.box = "ubuntu/xenial64"    				     # imagem do vagrant que será usada, ubuntu xenial
    docker.vm.box_check_update = false   			             # não procurar atualizações
    docker.vm.network "private_network", ip: "192.168.99.10", dns: "8.8.8.8" # definição de rede privada com endereço fixo
  end

#DEVOPS
  config.vm.define "devops" do |devops|                                      # configurar a definição de vm define chamada devops
    devops.vm.hostname = "devops"                                            # hostname da maquina
    devops.vm.box = "ubuntu/xenial64"                                        # imagem do vagrant que será usada, ubuntu xenial
    devops.vm.box_check_update = false                                       # não procurar atualizações
    devops.vm.network "private_network", ip: "192.168.99.11", dns: "8.8.8.8" # definição de rede privada com endereço fixo
  
    config.vm.provider "virtualbox" do |devops|                              # configurar a definição de vm provider chamada devops
      devops.memory = "3072"                                                 # definição de memoria da vm
    end
  end

#AUTOMATION
  config.vm.define "automation" do |automation|                                      # configurar a definição de vm chamada docker
    automation.vm.hostname = "automation"                                            # hostname da maquina
    automation.vm.box = "centos/7"                                            	     # imagem do vagrant que será usada, ubuntu xenial
    automation.vm.box_check_update = false                                           # não procurar atualizações
    automation.vm.network "private_network", ip: "192.168.99.12", dns: "8.8.8.8"     # definição de rede privada com endereço fixo
  end

end
