# hw1
[0.5] What is Docker, and how it differs from dependencies management systems? From virtual machines?

Когда есть необходимость более точно зафиксировать зависимости, более точно их изолировать и добиться большей воспроизводимости, используют либо виртуальные машины, либо контейнеры. В случае с виртуальными машинами над CPU стоит hypervisor (программа) - тонкая прослойка для нескольких операционных систем, которые работают одновременно. То есть наш компьютер шарится между несколькими операционными системами, и hypervisor обеспечивает возможность того, чтобы эти ОС могли запускать бинарные файлы на одном и том же компьютере. То есть мы обеспечиваем изоляцию на уровне всей ОС. Это довольно устаревший и тяжеловесный подход.


[0.5] What are the advantages and disadvantages of using containers over other approaches?

С точки зрения эффективности контейнеры котируются выше виртуальных машин. На одинаковом оборудовании можно запустить большое количество контейнеров, тогда как ВМ будет в разы меньше. 

Контейнеризация обеспечивает надежную изоляцию процессов и повышает уровень безопасности систем. Приложения, которые работают внутри контейнера, не имеют доступа к основной ОС и не могут на неё влиять.

Один контейнер соответствует одному запущенному процессу. Отключение отдельного контейнера для отладки или обновления никак не помешает нормальной работе всего приложения.

Для контейнеров характерен сравнительно короткий жизненный цикл. Любой контейнер можно остановить, перезапустить или уничтожить, если это необходимо. Данные, которые содержатся в контейнере, при этом тоже пропадут. 


[0.5] Explain how Docker works: what are Dockerfiles, how are containers created, and how are they run and destroyed?
[0.25] Name and describe at least one Docker competitor (i.e., a tool based on the same containerization technology).

Podman является еще одной платформой контейнерезации. По сравнению с Docker Podman является более безопасным за счет своих особенностей пользозвательских разрешений. Еще одним отличием от 

Podman is an open-source container engine, which performs much the same role as the Docker engine. It distinguishes itself because its isolation and user privilege features make Podman inherently more secure.

Equally, its command-line interface (CLI) commands are practically identical to those supported by the Docker CLI, with the exception that you’d use Podman in place of the Docker base.

Although Docker and Podman CLI commands are similar, knowing how to tell the difference between the two will help you when working with them behind the scenes. Docker follows the client/server model, using a daemon to manage all containers under its control. However, Podman, like rkt and LXC, functions without a central daemon. This can potentially improve the resilience of any given container by eliminating the possibility of a single point of failure (SPOF). In other words, if your daemon goes down, you’ll lose control over your containers. By contrast, in Podman, containers are self-sufficient, fully isolated environments, which can managed independent of one another.

Further, where Docker gives root permission to the container user by default, non-root access is standard in Podman.

[0.25] What is conda? How it differs from apt, yarn, and others?

**Conda** – это пакетный менеджер, который в отличие от других пакетных менеджеров может работать локально, то есть для каждого пользователя может работать независимо и не требовать системных прав. Конда работает на уровне бинарных файлов и библиотек внутри одного окружения.



 И пип и конда не имеют накладных расходов, но пользоваться ими неудобно, потому что большие программы, у них проблемы с точки зрения защищенности Поэтому современным подходом является изоляция окружения с помощью контейнера. Контейнер -- это метод изоляции зависимости. В нашей инфраструктуре есть ОС, которая знает штуку под нахванием Container Engine. У нас есть описание того что и как нужно установить в систему и то какой вид система приобретает после этого. Загружая это описание в контейнер engine мы можем запускать виртуальное окружение внутри системы. То есть у нас будет как бы своя копия внутри системы. Kernel умеет с ним работать и оно ничем не отличается от других копий системы, которые здесь могут быть дополнительно запущены (контейнеров). В этом контейнере сделали все, что нужно, не беспокоясь о проблемах с основной системой, и положили туда только тот файл, который нам нужен для работы. Отличие от гипервизора -- не делается отдельная копия ОС со всеми зависимостями под каждый контейнер. А одна ОС, в которой выделено ядро, которое умеет выделять память и другие базовые вещи необходимые для операционной системы. Это ядро может работать с многими окружениями, то есть нет нескольких тяжеловесных ОС, а одна ОС шарится. Примером container engine является docker. Это программа для набора кодов, которая взаимодействует с системой, чтобы создавать и удалять контейнеры.
