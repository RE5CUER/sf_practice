Vagrant.configure("2") do |config|
  #Зеркало доступное в РФ
  ENV['VAGRANT_SERVER_URL'] = 'https://vagrant.elab.pro'

  config.vm.box = "ubuntu/bionic64"

    #VirtualBox
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"    # Объем памяти в MB
    vb.cpus = 2           # Количество процессоров
  end

  #копируемый файл с хоста
  config.vm.synced_folder ".", "/vagrant"

  # Провиженинг
  config.vm.provision "shell", inline: <<-SHELL
    # Обновление пакетов
    apt-get update -y

    # Установка Python3, pip и библиотек
    apt-get install -y python3 python3-pip
    pip3 install psycopg2-binary django

    echo "Checking copied file..."
    ls -lh /vagrant/my_empty_file.txt
  SHELL
end
