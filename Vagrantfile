VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = 'fgrehm/centos-6-64-lxc'
  config.vm.box_version = '1.0.0'
  config.ssh.insert_key = false
  if Vagrant.has_plugin?('vagrant-hosts')
    config.vm.provision :hosts
  end

  RPM = 'haproxy-1.7.8-1.el6.x86_64.rpm'

  config.vm.define :haproxy do |instance|
    instance.vm.provision :shell, :args => [RPM], inline: <<-SHELL
      [ -f /vagrant/files/$1 ] || (cd /vagrant/files; wget http://au1.mirror.crc.id.au/repo/el6-extra/x86_64/$1)
      sudo rpm -U /vagrant/files/$1
      cp /vagrant/files/haproxy.cfg /etc/haproxy/haproxy.cfg
      service haproxy restart
    SHELL
  end

  config.vm.define :a do |instance|
    instance.vm.provision :shell, inline: <<-SHELL
      cp /vagrant/files/a.html index.html
      cp /vagrant/files/arandom.html random.html
      nohup python -m SimpleHTTPServer &> nohup.log &
    SHELL
  end

  config.vm.define :b do |instance|
    instance.vm.provision :shell, inline: <<-SHELL
      cp /vagrant/files/b.html index.html
      cp /vagrant/files/brandom.html random.html
      nohup python -m SimpleHTTPServer &> nohup.log &
    SHELL
  end
end
