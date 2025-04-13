
![image](https://github.com/user-attachments/assets/5c15f17b-b84e-4bf0-910c-8295e4518e53)



Установилваем Oracle linux и по инструкции устанавлиаем гостевые дополнения: 
[инструкция для VBoxGA.docx](https://github.com/user-attachments/files/18921020/VBoxGA.docx)

устанавливаем утилиты wget и curl
`sudo yum install wget`
![image](https://github.com/user-attachments/assets/1e5dff4e-c439-4516-9e3a-c52d6e751d73)

также устанавливаем утилиту curl `sudo yum install curl`
![image](https://github.com/user-attachments/assets/c0ed6478-ced3-4d1b-80ef-9a7d88569053)

далее скачиваем репозиторий с сайта `sudo wget -P /etc/yum.repos.d/ https://download.docker.com/linux/centos/docker-ce.repo`

![image](https://github.com/user-attachments/assets/6ec2c4c4-686d-4e0f-91a5-8774585cb06f)

Далее устанавливаем докер 
`sudo yum install docker-ce docker-ce-cli containerd.io`

![image](https://github.com/user-attachments/assets/4b8b5882-2b32-4cc3-9927-16eb9836b3cc)

Разрешаем автозапуск 
`sudo systemctl enable docker --now`

![image](https://github.com/user-attachments/assets/b345daa8-ac34-40e1-93f0-15bc7b3774ec)

смотрим номер последенй версии докера и записываем его в переменную COMVER 
`COMVER=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep 'tag_name' | cut -d\" -f4)`

![image](https://github.com/user-attachments/assets/74ffe420-39b3-4eab-85ea-4448c6e007e6)

копируем репозиторий 
`git clone https://github.com/skl256/grafana_stack_for_docker.git`

![image](https://github.com/user-attachments/assets/afe1886d-199d-476d-b9fe-592a66d0995c)

переходим в папку grafana_stack_for_docker
`cd grafana_stack_for_docker`
и создаем там новый дерикторий 
`sudo mkdir -p /mnt/common_volume/swarm/grafana/config`

![image](https://github.com/user-attachments/assets/1be2029c-5da2-4765-a743-e7aca93844ef)

создаем место хранения файлов Grafana и Prometheus 
`sudo mkdir -p /mnt/common_volume/grafana/{grafana-config,grafana-data,prometheus-data}`

![image](https://github.com/user-attachments/assets/7becc57d-f7fa-4033-bfcb-c8b3d279d84d)

создаем новый файл grafana.ini
`touch /mnt/common_volume/grafana/grafana-config/grafana.ini`

![image](https://github.com/user-attachments/assets/da047cbb-3f50-4416-bd3c-58fa13260deb)

копируем все файлы и подкаталоги из каталога config/ в каталог /mnt/common_volume/swarm/grafana/config/
`cp config/* /mnt/common_volume/swarm/grafana/config/`

![image](https://github.com/user-attachments/assets/71375922-b365-4da7-a6d4-083bc8137636)

переименовываем файл
`mv grafana.yaml docker-compose.yaml`
![image](https://github.com/user-attachments/assets/bc080ba1-9faf-4159-bfa8-5e60545ff408)

поднимаем докер
`sudo docker compose up -d`

![image](https://github.com/user-attachments/assets/7d83538f-4f71-41d0-b4d5-2f29ae43d9db)

переходим в файл и вносим там изменения
`sudo vi docker-compose.yaml`

![image](https://github.com/user-attachments/assets/6964ded9-e38f-4034-9be4-573561cabb27)

также делаем с следующим файлом
`sudo vi prometheus.yaml`

Далее переходим на сайт localhost:3000
логи и пароль admin

далее создаем новый dashboard

![image](https://github.com/user-attachments/assets/6ec90086-ba34-4ea8-a174-d13b741401c5)

выбираем add visualization

![image](https://github.com/user-attachments/assets/5c488116-2ffc-4143-8e42-05c0619f0270)

![image](https://github.com/user-attachments/assets/ab848153-e388-4230-96e7-4e1cd04aa2fb)

выбираем Prometheus

![image](https://github.com/user-attachments/assets/eef6e5f1-2911-41d5-8a30-4602f87a2d4d)

вводим данные

![image](https://github.com/user-attachments/assets/f8b1b20e-e3c7-4337-9f22-eb1e5a76b21f)
![image](https://github.com/user-attachments/assets/a8397033-85c6-402e-9c79-24e01c455de9)

возращаемся назад и выбираем import

![image](https://github.com/user-attachments/assets/a064d256-d16c-4d6d-8b27-940303729ee9)

выбираем свое

![image](https://github.com/user-attachments/assets/ca816ed7-fbd7-4d46-8672-c781e590fbd6)

и нажимаем import


