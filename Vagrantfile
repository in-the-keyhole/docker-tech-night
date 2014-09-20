# -*- mode: ruby -*-
# vi: set ft=ruby :

# a big ol' mess of inline script.  yay!
$provisioning_script = <<SCRIPT
if [ ! -f /provisioning_script_has_already_been_applied ];
then
    echo "---------- provisioning script running... ----------"
    # https://sipb.mit.edu/doc/safe-shell/
    set -eufx -o pipefail
    apt-get update
    # install some general tools
    apt-get install --yes git tree htop
    # install fig
    curl -L https://github.com/docker/fig/releases/download/0.5.2/linux > /usr/local/bin/fig
    chmod +x /usr/local/bin/fig
    # install nodejs
    apt-get install --yes software-properties-common python-software-properties
    add-apt-repository ppa:chris-lea/node.js
    apt-get update
    apt-get install --yes nodejs
    # install prerequisite(s) for codebox
    apt-get install --yes build-essential
    # install codebox
    npm install -g codebox@0.8.1
    # configure supervisor
    mkdir --parents /etc/supervisor/conf.d
    echo "[inet_http_server]" > /etc/supervisor/conf.d/custom.conf
    echo "port=*:9001" >> /etc/supervisor/conf.d/custom.conf
    echo "[program:codebox]" >> /etc/supervisor/conf.d/custom.conf
    echo "command=codebox run /vagrant --port 80 --title 'Keyhole Docker Tech Night' --email noreply@keyholesoftware.com" >> /etc/supervisor/conf.d/custom.conf
    echo "environment=HOME="/home"" >> /etc/supervisor/conf.d/custom.conf
    echo "autorestart=true" >> /etc/supervisor/conf.d/custom.conf
    # install and start supervisor
    apt-get install --yes supervisor
    # all done
    touch /provisioning_script_has_already_been_applied
    set +x
    echo " ---------- provisioning script finished... ----------"
else
    echo "provisioning script has already been run, skipping..."
fi
SCRIPT


VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "phusion/ubuntu-14.04-amd64"
  config.vm.network "private_network", ip: "192.168.169.170"
  config.vm.provision "shell", inline: $provisioning_script
  config.vm.provision "docker",
      images: [ "ubuntu:14.04",
                "centos:centos7",
                "wordpress:3.9.2",
                "mysql:5.7.4",
                "mongo:2.7.5",
                "node:0.10.30",
                "java:8u40" ]

end
