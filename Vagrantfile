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
MIIEpAIBAAKCAQEA+iczCndNWhxD1YtCxkk8Uog2VIjlVcfUZMHgW0IBVKuquEN/
6fI64vmB+HtXPSGVhMWkxfSBVZdr3vJbui7WWlasSQPvoLLfqK8tWlubRiYqUCwu
rsIPNA6cN22W3bRO0ecCArbH5ueseh3V4C47HG4L/myxqQuxX/n8WQraj0+1vbbp
jiwDQEk/xIftcuyYK0mwHL1HG1sSP9v/9yl1ccNIp9Xz7OpYrT8UfIlH71LpEu/8
Bjxe6oIsWM9tbkyDSPy9+9TDxdyuN47bghJ3lqJYfnOP0MNhY7HAToVnxvmIQ30X
IjShj5CiLiN7cbo+sRSJ8KoZHIji1zKeF2EciwIDAQABAoIBAQCjFI0U5KP7+/NJ
MwmsRTBbScvJnpmMK8NOkIpYVBaUAXpBuFeax70WHb1apeZAxzU3orYCC52JlDbR
2MRuA3zg1iJpU3SUGijvSozRnGkE+XqaW8NvULoioOe8xugUzyiXdPd9l3WJFj3+
OpclGF6W8TNGgcvsvd+8Bzg5QHct92o6RSp3fYs1G3gSnw9BtJmDTFLoRzBo+NLQ
Kzp32cf1DO4xcc2ZA7pvUZu3YYULBJx6T7W1pjAkXfGSfJYpKjrXTX7W9Gm7/QRp
bm4/JsxxdR2IEsa+AjyN9S7QDp7K0490eqgl6Z8tHteLBDpaD1bNF6cpvUqNLXil
/IMP+AUhAoGBAP3LIJR5wpGhwIFoCMquSkN6qGdcZ9iotiUKu7yRLp2RKmI+XHkU
KVF6/0Bc3X19MsZ8nci0Qr9JcMXt5A/xIDLPw2NNIHD1SvqNyizj4qpYqPXNgMtD
Z6UaOJXUH7HY0hrszRxBMlKvPvgcvRp/QKFN8Eyq9WD6vetPaDkNXSaRAoGBAPxT
+ECGHk1oKRJCEOMketyJbr33JvX5vwKdxdAoTf+tCdaSy0efsrR6peksSdQEej4x
IVxyIjy+N7TAgWPjwzM001Y7256gbSxgnwmZm9SZNs02Yk/4ijj5sabuucVI3KRD
6hc9obtLJx/frmdtt2c07hV3YyUh1atZDCwmZ3dbAoGANQy3o7GL5SsddS9M3yjt
ZwuFlg1vu48Qe8+xjGoAh3knld+ZLsnzFRATuN1wguGfsnOr+58KcLemNglS6a4q
X9Sj7+bYSCRN5u+qehWsdJURxEePi21shctkVpU/hspeqLgk66oJHdV54R0Ivjgp
R05mU3BM2FexSTWRAJP1i7ECgYEA4VmU4vtk4LjfxWCfeFzCJWfQMXQjpZZwksOZ
QPheALPnj2z2g3cKwMiwl/hnzyRYkGaMZuW/0gQH+DPc2vs0/+xzuhYnZBnepr18
C7TWSR60pL2nO8i6mXvWv0GBQ8J423OUA0GVyZGq1XqNZe3E2DWbVCyVrTn0e91B
U8TQrvUCgYARfqS8tpN67LCPsU8mWPcVpTlUwTow8gEPJcALfVvmurt7uy3vnhuh
tCsv+OlrQ9AKWwJEFvkv4m5OCtIn7Ntt6wY3kOUAGMZsKfV7n1z6RKzJG68BAMd1
bX9FRzLprC1UV319nVhqPi7sFGXEYNdWLA/kP8vYi8oigA5EG3HQMg==
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
