# Puppet


## Context

This lab is developed in AWS with Ubuntu server.

## Puppet Server

sudo apt-get update
sudo apt-get install wget
wget https://apt.puppetlabs.com/puppet-release-bionic.deb
sudo dpkg -i puppet-release-bionic.deb
sudo apt-get install puppetmaster
apt policy puppetmaster
sudo systemctl status puppet-master.service
sudo vi /etc/default/puppet-master
JAVA_ARGS="-Xms512m -Xmx512m"
sudo systemctl restart puppet-master.service
sudo ufw allow 8140/tcp

sudo vi /etc/hosts

## Puppet Agent

sudo apt-get update
sudo apt-get install wget
wget https://apt.puppetlabs.com/puppet-release-bionic.deb
sudo dpkg -i puppet-release-bionic.deb
sudo apt-get install puppet

sudo systemctl start puppet
sudo systemctl enable puppet


## Puppet class at Server

sudo mkdir -p /etc/puppet/code/environments/production/manifests/
sudo vi /etc/puppet/code/environments/production/manifests/site.pp

file {'/tmp/it_works.txt':
	ensure  => present,
	mode    => '0644',
	content => "It works on ${ipaddress_eth0!}\n",
    }


sudo systemctl restart puppet-master


