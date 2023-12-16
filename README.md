# lesson15

**Домашнее задание**

-Запретить всем пользователям, кроме группы admin логин в выходные (суббота и воскресенье), без учета праздников

Работа проводилась на centos 8 stream 20230501.0

Подключился к VM, создал пользователей, группу, добавил user-ов в группу

      sudo useradd otusadm && sudo useradd otus
      
      echo "Otus2022!" | sudo passwd --stdin otusadm && echo "Otus2022!" | sudo passwd --stdin otus
      
      sudo groupadd -f admin
      
      usermod otusadm -a -G admin && usermod root -a -G admin && usermod vagrant -a -G admin

![image](https://github.com/movik242/lesson15/assets/143793993/7317fce0-6b59-4bae-ab41-00d6b4f78e65)

Проверил, что юзеры подключаются

![image](https://github.com/movik242/lesson15/assets/143793993/83e2628d-c603-45b3-8d37-35933490af26)

Проверил, кто входит в группу admin

![image](https://github.com/movik242/lesson15/assets/143793993/05ec056b-4404-4906-b6bb-e7b40a8a63cf)

Настроил скрипт для запрета на подключение в выходные дни

Добавил права на исполнение файла: 

    chmod +x /usr/local/bin/login.sh

Добавил выполнение скрипта

    vi /etc/pam.d/sshd

![image](https://github.com/movik242/lesson15/assets/143793993/f21f4ff1-8484-4074-b119-b5a02aff3c3f)

сегодня суббота, сделал проверку доступа

![image](https://github.com/movik242/lesson15/assets/143793993/c264eaea-78f3-4462-8c80-a18d12303c74)






