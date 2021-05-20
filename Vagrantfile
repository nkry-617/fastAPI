$script = <<-'SCRIPT'
apt update
apt install -y python3-pip language-pack-ja sqlite3
echo 'alias python="python3"' >> /home/vagrant/.bashrc
echo 'alias pip="pip3"' >> /home/vagrant/.bashrc
pip install --upgrade pip
pip3 install fastapi sqlalchemy uvicorn Jinja2 python-multipart
touch /fastAPI_Tutorial/controllers.py
SCRIPT
Vagrant.configure("2") do |config|
 config.vm.box = "bento/ubuntu-18.04"
 config.vm.network "forwarded_port", guest: 8000, host: 8000
 config.vm.synced_folder ".", "/vagrant", disabled: true
 config.vm.synced_folder "./fastAPI_Tutorial", "/fastAPI_Tutorial",create: true
 config.vm.provision :shell, inline: $script, privileged: true
end
