# Домашнее задание к занятию "`Уязвимости и атаки на информационные системы`" - `Мурчин Артем`

### Задание 1

Скачайте и установите виртуальную машину Metasploitable: https://sourceforge.net/projects/metasploitable/.

Это типовая ОС для экспериментов в области информационной безопасности, с которой следует начать при анализе уязвимостей.

Просканируйте эту виртуальную машину, используя **nmap**.

Попробуйте найти уязвимости, которым подвержена эта виртуальная машина.

Сами уязвимости можно поискать на сайте https://www.exploit-db.com/.

Для этого нужно в поиске ввести название сетевой службы, обнаруженной на атакуемой машине, и выбрать подходящие по версии уязвимости.

Ответьте на следующие вопросы:

- Какие сетевые службы в ней разрешены?
- Какие уязвимости были вами обнаружены? (список со ссылками: достаточно трёх уязвимостей)
  
*Приведите ответ в свободной форме.* 

### Решение 1

![alt text](https://github.com/artmur1/13-01-hw/blob/main/1.png)

Просканировал Metasploitable с помощию nmap -sV.

Разрешены следующие сетевые службы: ftp, ssh, telnet, smtp, domain, http, rpcbind, netbios-ssn, exec, login, tcpwrapped, java-rmi, bindshell, nfs, ftp, mysql, postgresql, vnc, X11, irc, ajp13, http.

![alt text](https://github.com/artmur1/13-01-hw/blob/main/2.png)

![alt text](https://github.com/artmur1/13-01-hw/blob/main/3.png)

Были обнаружены следующие уязвимости:

vsftpd 2.3.4 https://www.exploit-db.com/exploits/49757

OpenSSH 4.7p1 https://www.exploit-db.com/exploits/15215

BIND 9.4.2 https://www.exploit-db.com/exploits/6122

PostgreSQL DB 8.3.0 - 8.3.7 https://www.exploit-db.com/exploits/7855

### Задание 2

Проведите сканирование Metasploitable в режимах SYN, FIN, Xmas, UDP.

Запишите сеансы сканирования в Wireshark.

Ответьте на следующие вопросы:

- Чем отличаются эти режимы сканирования с точки зрения сетевого трафика?
- Как отвечает сервер?

*Приведите ответ в свободной форме.*

### Решение 2

![alt text](https://github.com/artmur1/13-01-hw/blob/main/2-1-syn.png)

Сканирование Metasploitable в режиме SYN.

Отправляется по TCP запрос [SYN] и получаем от Metasploitable по TCP ответ [RST], [RST, ASK]. 

---

![alt text](https://github.com/artmur1/13-01-hw/blob/main/2-2-fin.png)

Сканирование Metasploitable в режиме FIN.

Отправляется по TCP запрос [ASK] и получаем от Metasploitable по TCP ответ [RST].

---

![alt text](https://github.com/artmur1/13-01-hw/blob/main/2-3-Xmas.png)

Сканирование Metasploitable в режиме Xmas

Отправляется по TCP запрос [FIN, PSH, URG] и получаем от Metasploitable по TCP ответ [RST, ASK].

---

![alt text](https://github.com/artmur1/13-01-hw/blob/main/2-4-UDP.png)

Сканирование Metasploitable в режиме UDP

Идет сканирование целой кучи UDP портов. Есть запросы по ICMP.
