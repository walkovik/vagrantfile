# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
# /*=====================================
# =            FREE VERSION!            =
# =====================================*/
# This is the free (still awesome) version of Scotch Box.
# Please go Pro to support the project and get more features.
# Check out https://box.scotch.io to learn more. Thanks

config.vm.box = "scotch/box"
config.vm.network "private_network", ip: "192.168.33.10"
config.vm.hostname = "scotchbox"
config.vm.synced_folder ".", "/var/www", :mount_options => ["dmode=777", "fmode=666"]

# Optional NFS. Make sure to remove other synced_folder line too
#config.vm.synced_folder ".", "/var/www", :nfs => { :mount_options => ["dmode=777","fmode=666"] }


# Begin Edits by Eduardo Sanchez, UI improves
# The line below changes the name of the host from "default" to LTUR
# These lines should be updated according to each web property
config.vm.define "LTUR" do |ltur|
end
# Now, we change the name of the Box in the VBox App
config.vm.provider :virtualbox do |vb|
	vb.name = "LTUR"
end
# Now, we add a custom message to the user, so he may know which port is going to be used
#in order to run multiple boxes at a time
config.vm.post_up_message = "Run your website or app at http://192.168.33.10"
# Now, we provision the machine with some updates to the scotch/box
# Please note the change of default folder
config.vm.provision "shell", inline: <<-SHELL
	sudo sed -i s,/var/www/public,/var/www,g /etc/apache2/sites-available/000-default.conf
	sudo sed -i s,/var/www/public,/var/www,g /etc/apache2/sites-available/scotchbox.local.conf
	sudo service apache2 restart
SHELL

end
# End Eduardo Sanchez Edits