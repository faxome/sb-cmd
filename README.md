Развертывание сервиса
=========

Все необходимое устанавливается после запуска роли build, для запуска необходимо выполнить команду:

ansible-playbook build_playbook

В результате будет установлен nginx, созданы службы balance и app для управления, создана рабочая папка, 
скопированы необходмые для запуска web-сервиса файлы, установлены зависимости.


Управление сервисом
=========
Для управления всем продуктом предусмотрен общий playbook, доступны следующие команды для управления:

state - состояние, предусмотрено 3 параметра [started | stopped | restarted]

#example
ansible-playbook allmanage_play --extra-vars "state=stopped all=custom"

serv - служба, имеет два параметра [balance | app]

#example
ansible-playbook allmanage_play --extra-vars "state=stopped serv=balance"

nodes - переменная позволяющая задать два параметра all - выполнить везде, custom - выполнить для указанных сервисов

#example
ansible-playbook allmanage_play --extra-vars "state=stopped all=all"


Роль для управления приложением
=========
state - состояние, предусмотрено 3 параметра [started | stopped | restarted]

#example
ansible-playbook app_manage_play --extra-vars "state=stopped"


Роль для управления балансировщиками
=========
state - состояние, предусмотрено 3 параметра [started | stopped | restarted]

#example
ansible-playbook balance_manage_play --extra-vars "state=restarted"
