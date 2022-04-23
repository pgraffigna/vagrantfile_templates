# vagrant_template

Templates para desplegar entornos de prueba usando vagrant.

---

### vagrant plugins

- vagrant plugin install vagrant-hostmanager

```ruby
if Vagrant.has_plugin?("vagrant-hostmanager")
   config.hostmanager.enabled = true
   config.hostmanager.manage_host = true
   config.hostmanager.ignore_private_ip = false
   config.hostmanager.include_offline = true
   end
```   
- vagrant plugin install vagrant-cachier

```ruby
if Vagrant.has_plugin?("vagrant-cachier")
    config.cache.scope = :box
    config.cache.synced_folder_opts = {
      type: :nfs,
      mount_options: ['rw', 'vers=3', 'tcp', 'nolock'] }
  end
```
- vagrant plugin install vagrant-vbguest

```ruby
  unless Vagrant.has_plugin?("vagrant-vbguest")
    puts 'Instalando el plugin vagrant-vbguest ...'
    system('vagrant plugin install vagrant-vbguest')
  end
```
- vagrant plugin install vagrant-docker-compose

```ruby
  unless Vagrant.has_plugin?("vagrant-docker-compose")
    puts 'Instalando el plugin vagrant-docker-compose ...'
    system('vagrant plugin install vagrant-docker-compose')
  end
```