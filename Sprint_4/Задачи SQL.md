## Консоль

* Задание 1
  
От разработчиков поступила задача: нужно выяснить, какие запросы шли с IP-адреса. IP-адрес состоит из четырёх чисел, они разделены точками. Тебе нужны адреса, которые начинаются с «233.201.».
Логи лежат на удалённом сервере по адресу logs/2019/12. День, когда случилась ошибка, неизвестен. 
Твоя задача — узнать, какие запросы были отправлены. 
  
Команда или последовательность команд, которой удалось получить нужные логи:
 
cd logs/2019/12 
grep -R "^233.201."

Логи:
233.201.188.154 - - [18/12/2019:21:46:01 +0000] "DELETE /events HTTP/1.1" 403 3971
233.201.182.9 - - [21/12/2019:21:56:20 +0000] "PATCH /users HTTP/1.1" 400 4118


* Задание 2

В системе обнаружен баг. Он проявлялся 30.12.2019 и 31.12.2019 с 21:30:00 до 21:39:59. При этом появлялись ошибки с номерами 400 и 500. Твоя задача — сохранить в отдельный файл логи, которые были записаны в этот период.  
Затем эти логи надо разложить по отдельным файлам: логи с одинаковой ошибкой положи в один файл. Как это сделать:
В домашней директории на удалённом сервере создай директорию bug1.
Все запросы, которые произошли в указанный период, положи в файл main.txt в директорию bug1.
Внутри директории bug1 создай директорию events.
Внутри директории events создай файлы для ошибок с номерами 400 и 500. Назови эти файлы 400.txt и 500.txt соответственно. В них выдели логи с соответствующей ошибкой из файла main.txt.

Команды, которые создают директории bug1 и events:

mkdir bug1
mkdir bug1/events
Команда, которой выбираешь запросы за указанный период. Это те запросы, которыми ты отбираешь логи в файл main.txt:

grep -R "3./12/2019:21:3.:.." ~/logs/2019/12/ > bug1/main.txt
Команды, которыми ты кладёшь логи в файлы 400.txt и 500.txt из main.txt:

grep " 400 " bug1/main.txt > bug1/events/400.txt
grep " 500 " bug1/main.txt > bug1/events/500.txt
400.txt
/home/morty/logs/2019/12/apache_2019-12-31.txt:86.34.86.182 - - [31/12/2019:21:35:10 +0000] "POST /auth HTTP/1.1" 400 3626
/home/morty/logs/2019/12/apache_2019-12-31.txt:167.37.16.117 - - [31/12/2019:21:35:17 +0000] "PATCH /customers HTTP/1.1" 400 3294
/home/morty/logs/2019/12/apache_2019-12-31.txt:199.128.92.19 - - [31/12/2019:21:35:43 +0000] "PUT /users HTTP/1.1" 400 4180
/home/morty/logs/2019/12/apache_2019-12-31.txt:162.152.99.143 - - [31/12/2019:21:35:59 +0000] "PUT /users HTTP/1.1" 400 4606
/home/morty/logs/2019/12/apache_2019-12-31.txt:83.115.59.224 - - [31/12/2019:21:37:26 +0000] "GET /alerts HTTP/1.1" 400 3489
/home/morty/logs/2019/12/apache_2019-12-31.txt:194.10.97.226 - - [31/12/2019:21:37:31 +0000] "DELETE /lists HTTP/1.1" 400 2447
/home/morty/logs/2019/12/apache_2019-12-31.txt:180.99.214.40 - - [31/12/2019:21:37:44 +0000] "DELETE /alerts HTTP/1.1" 400 2077
/home/morty/logs/2019/12/apache_2019-12-31.txt:154.152.205.4 - - [31/12/2019:21:37:50 +0000] "GET /playbooks HTTP/1.1" 400 3324
/home/morty/logs/2019/12/apache_2019-12-31.txt:197.82.125.54 - - [31/12/2019:21:37:52 +0000] "PUT /fieldsets HTTP/1.1" 400 4365
/home/morty/logs/2019/12/apache_2019-12-31.txt:115.89.87.219 - - [31/12/2019:21:38:06 +0000] "PUT /playbooks HTTP/1.1" 400 2589
/home/morty/logs/2019/12/apache_2019-12-31.txt:100.77.15.14 - - [31/12/2019:21:38:07 +0000] "GET /fieldsets HTTP/1.1" 400 4911
/home/morty/logs/2019/12/apache_2019-12-31.txt:22.33.159.242 - - [31/12/2019:21:38:07 +0000] "GET /playbooks HTTP/1.1" 400 3955
/home/morty/logs/2019/12/apache_2019-12-31.txt:149.148.229.11 - - [31/12/2019:21:39:16 +0000] "GET /users HTTP/1.1" 400 2071
/home/morty/logs/2019/12/apache_2019-12-31.txt:236.107.64.192 - - [31/12/2019:21:39:17 +0000] "PATCH /users HTTP/1.1" 400 2791
/home/morty/logs/2019/12/apache_2019-12-31.txt:24.156.105.39 - - [31/12/2019:21:39:23 +0000] "GET /lists HTTP/1.1" 400 2902
/home/morty/logs/2019/12/apache_2019-12-31.txt:193.50.164.254 - - [31/12/2019:21:39:23 +0000] "PUT /playbooks HTTP/1.1" 400 3296
/home/morty/logs/2019/12/apache_2019-12-31.txt:18.123.104.91 - - [31/12/2019:21:39:52 +0000] "GET /collectors HTTP/1.1" 400 4372
/home/morty/logs/2019/12/apache_2019-12-31.txt:234.218.148.4 - - [31/12/2019:21:39:54 +0000] "PUT /users HTTP/1.1" 400 2509
/home/morty/logs/2019/12/apache_2019-12-30.txt:80.57.170.51 - - [30/12/2019:21:35:12 +0000] "DELETE /users HTTP/1.1" 400 3623
/home/morty/logs/2019/12/apache_2019-12-30.txt:204.235.176.118 - - [30/12/2019:21:35:13 +0000] "POST /users HTTP/1.1" 400 4704
/home/morty/logs/2019/12/apache_2019-12-30.txt:82.95.203.67 - - [30/12/2019:21:35:19 +0000] "DELETE /lists HTTP/1.1" 400 3737
/home/morty/logs/2019/12/apache_2019-12-30.txt:155.242.215.46 - - [30/12/2019:21:35:38 +0000] "POST /playbooks HTTP/1.1" 400 4450
/home/morty/logs/2019/12/apache_2019-12-30.txt:189.176.85.0 - - [30/12/2019:21:35:39 +0000] "PATCH /alerts HTTP/1.1" 400 2732
/home/morty/logs/2019/12/apache_2019-12-30.txt:13.108.71.71 - - [30/12/2019:21:35:43 +0000] "PATCH /events HTTP/1.1" 400 3410
/home/morty/logs/2019/12/apache_2019-12-30.txt:195.213.133.182 - - [30/12/2019:21:35:46 +0000] "PUT /customers HTTP/1.1" 400 3085
/home/morty/logs/2019/12/apache_2019-12-30.txt:235.243.133.78 - - [30/12/2019:21:35:47 +0000] "PATCH /customers HTTP/1.1" 400 3264
/home/morty/logs/2019/12/apache_2019-12-30.txt:192.57.115.49 - - [30/12/2019:21:35:55 +0000] "POST /parsers HTTP/1.1" 400 2457
/home/morty/logs/2019/12/apache_2019-12-30.txt:71.0.49.244 - - [30/12/2019:21:35:55 +0000] "PUT /collectors HTTP/1.1" 400 2785
/home/morty/logs/2019/12/apache_2019-12-30.txt:224.159.206.126 - - [30/12/2019:21:36:02 +0000] "DELETE /customers HTTP/1.1" 400 4569
/home/morty/logs/2019/12/apache_2019-12-30.txt:131.35.106.246 - - [30/12/2019:21:36:04 +0000] "DELETE /lists HTTP/1.1" 400 2578
/home/morty/logs/2019/12/apache_2019-12-30.txt:216.24.42.208 - - [30/12/2019:21:36:06 +0000] "GET /parsers HTTP/1.1" 400 4597
/home/morty/logs/2019/12/apache_2019-12-30.txt:123.53.150.160 - - [30/12/2019:21:37:19 +0000] "PATCH /events HTTP/1.1" 400 4379
/home/morty/logs/2019/12/apache_2019-12-30.txt:61.129.127.103 - - [30/12/2019:21:37:32 +0000] "GET /lists HTTP/1.1" 400 2575
/home/morty/logs/2019/12/apache_2019-12-30.txt:90.216.4.78 - - [30/12/2019:21:37:34 +0000] "PATCH /lists HTTP/1.1" 400 3899
/home/morty/logs/2019/12/apache_2019-12-30.txt:204.250.214.208 - - [30/12/2019:21:37:36 +0000] "PATCH /parsers HTTP/1.1" 400 4742
/home/morty/logs/2019/12/apache_2019-12-30.txt:79.214.240.98 - - [30/12/2019:21:37:37 +0000] "POST /fieldsets HTTP/1.1" 400 4441
/home/morty/logs/2019/12/apache_2019-12-30.txt:65.47.42.12 - - [30/12/2019:21:37:39 +0000] "PATCH /customers HTTP/1.1" 400 2500
/home/morty/logs/2019/12/apache_2019-12-30.txt:251.118.141.34 - - [30/12/2019:21:37:41 +0000] "POST /customers HTTP/1.1" 400 3519
/home/morty/logs/2019/12/apache_2019-12-30.txt:205.20.166.196 - - [30/12/2019:21:37:51 +0000] "POST /users HTTP/1.1" 400 4032
/home/morty/logs/2019/12/apache_2019-12-30.txt:156.217.3.46 - - [30/12/2019:21:37:52 +0000] "PATCH /parsers HTTP/1.1" 400 2020
/home/morty/logs/2019/12/apache_2019-12-30.txt:48.240.198.167 - - [30/12/2019:21:37:57 +0000] "PATCH /playbooks HTTP/1.1" 400 4100
/home/morty/logs/2019/12/apache_2019-12-30.txt:101.255.159.211 - - [30/12/2019:21:37:59 +0000] "GET /auth HTTP/1.1" 400 2324
/home/morty/logs/2019/12/apache_2019-12-30.txt:80.76.98.203 - - [30/12/2019:21:38:00 +0000] "POST /playbooks HTTP/1.1" 400 3045
/home/morty/logs/2019/12/apache_2019-12-30.txt:85.64.63.255 - - [30/12/2019:21:38:13 +0000] "PATCH /collectors HTTP/1.1" 400 2291
/home/morty/logs/2019/12/apache_2019-12-30.txt:184.79.247.161 - - [30/12/2019:21:38:13 +0000] "PUT /alerts HTTP/1.1" 400 3557
/home/morty/logs/2019/12/apache_2019-12-30.txt:93.2.134.22 - - [30/12/2019:21:39:39 +0000] "DELETE /alerts HTTP/1.1" 400 3701

500.txt.

/home/morty/logs/2019/12/apache_2019-12-31.txt:208.205.133.127 - - [31/12/2019:21:35:17 +0000] "DELETE /alerts HTTP/1.1" 500 4561
/home/morty/logs/2019/12/apache_2019-12-31.txt:20.145.255.91 - - [31/12/2019:21:35:30 +0000] "GET /parsers HTTP/1.1" 500 3051
/home/morty/logs/2019/12/apache_2019-12-31.txt:91.66.134.13 - - [31/12/2019:21:35:53 +0000] "POST /lists HTTP/1.1" 500 3319
/home/morty/logs/2019/12/apache_2019-12-31.txt:31.88.211.206 - - [31/12/2019:21:35:57 +0000] "DELETE /events HTTP/1.1" 500 2325
/home/morty/logs/2019/12/apache_2019-12-31.txt:171.37.114.114 - - [31/12/2019:21:37:39 +0000] "DELETE /fieldsets HTTP/1.1" 500 3253
/home/morty/logs/2019/12/apache_2019-12-31.txt:223.157.242.167 - - [31/12/2019:21:37:59 +0000] "POST /users HTTP/1.1" 500 2283
/home/morty/logs/2019/12/apache_2019-12-31.txt:98.181.102.34 - - [31/12/2019:21:38:06 +0000] "PATCH /fieldsets HTTP/1.1" 500 4672
/home/morty/logs/2019/12/apache_2019-12-31.txt:254.74.22.79 - - [31/12/2019:21:38:06 +0000] "PUT /lists HTTP/1.1" 500 2259
/home/morty/logs/2019/12/apache_2019-12-31.txt:103.46.238.3 - - [31/12/2019:21:38:09 +0000] "PUT /lists HTTP/1.1" 500 3992
/home/morty/logs/2019/12/apache_2019-12-31.txt:41.62.205.107 - - [31/12/2019:21:39:20 +0000] "PATCH /alerts HTTP/1.1" 500 3631
/home/morty/logs/2019/12/apache_2019-12-31.txt:22.53.105.197 - - [31/12/2019:21:39:31 +0000] "DELETE /collectors HTTP/1.1" 500 4202
/home/morty/logs/2019/12/apache_2019-12-31.txt:178.22.133.42 - - [31/12/2019:21:39:43 +0000] "PUT /alerts HTTP/1.1" 500 4648
/home/morty/logs/2019/12/apache_2019-12-31.txt:102.247.13.50 - - [31/12/2019:21:39:55 +0000] "PATCH /auth HTTP/1.1" 500 3736
/home/morty/logs/2019/12/apache_2019-12-30.txt:64.250.112.189 - - [30/12/2019:21:35:13 +0000] "PUT /parsers HTTP/1.1" 500 4639
/home/morty/logs/2019/12/apache_2019-12-30.txt:193.253.101.180 - - [30/12/2019:21:35:31 +0000] "PATCH /alerts HTTP/1.1" 500 2944
/home/morty/logs/2019/12/apache_2019-12-30.txt:197.106.117.194 - - [30/12/2019:21:35:31 +0000] "PATCH /parsers HTTP/1.1" 500 3519
/home/morty/logs/2019/12/apache_2019-12-30.txt:247.124.71.67 - - [30/12/2019:21:35:45 +0000] "PUT /alerts HTTP/1.1" 500 2746
/home/morty/logs/2019/12/apache_2019-12-30.txt:62.88.204.119 - - [30/12/2019:21:35:51 +0000] "PUT /auth HTTP/1.1" 500 2666
/home/morty/logs/2019/12/apache_2019-12-30.txt:125.156.142.26 - - [30/12/2019:21:36:01 +0000] "PATCH /events HTTP/1.1" 500 3460
/home/morty/logs/2019/12/apache_2019-12-30.txt:144.170.212.70 - - [30/12/2019:21:36:04 +0000] "DELETE /parsers HTTP/1.1" 500 2599
/home/morty/logs/2019/12/apache_2019-12-30.txt:59.39.200.252 - - [30/12/2019:21:36:05 +0000] "GET /alerts HTTP/1.1" 500 2650
/home/morty/logs/2019/12/apache_2019-12-30.txt:150.136.200.100 - - [30/12/2019:21:37:24 +0000] "POST /lists HTTP/1.1" 500 2684
/home/morty/logs/2019/12/apache_2019-12-30.txt:84.81.25.45 - - [30/12/2019:21:37:25 +0000] "POST /auth HTTP/1.1" 500 2052
/home/morty/logs/2019/12/apache_2019-12-30.txt:30.222.160.141 - - [30/12/2019:21:37:30 +0000] "PATCH /parsers HTTP/1.1" 500 2017
/home/morty/logs/2019/12/apache_2019-12-30.txt:117.87.158.36 - - [30/12/2019:21:37:34 +0000] "POST /fieldsets HTTP/1.1" 500 4056
/home/morty/logs/2019/12/apache_2019-12-30.txt:212.153.128.212 - - [30/12/2019:21:37:42 +0000] "PUT /fieldsets HTTP/1.1" 500 3259
/home/morty/logs/2019/12/apache_2019-12-30.txt:58.188.83.217 - - [30/12/2019:21:37:46 +0000] "POST /playbooks HTTP/1.1" 500 3947
/home/morty/logs/2019/12/apache_2019-12-30.txt:193.123.131.146 - - [30/12/2019:21:37:47 +0000] "PUT /lists HTTP/1.1" 500 3902
/home/morty/logs/2019/12/apache_2019-12-30.txt:182.7.179.91 - - [30/12/2019:21:37:48 +0000] "GET /users HTTP/1.1" 500 2950
/home/morty/logs/2019/12/apache_2019-12-30.txt:10.25.168.164 - - [30/12/2019:21:38:05 +0000] "PATCH /playbooks HTTP/1.1" 500 3858
/home/morty/logs/2019/12/apache_2019-12-30.txt:215.201.210.173 - - [30/12/2019:21:38:11 +0000] "PATCH /customers HTTP/1.1" 500 3277
/home/morty/logs/2019/12/apache_2019-12-30.txt:179.241.103.167 - - [30/12/2019:21:39:23 +0000] "POST /lists HTTP/1.1" 500 3669
/home/morty/logs/2019/12/apache_2019-12-30.txt:147.188.170.252 - - [30/12/2019:21:39:33 +0000] "POST /fieldsets HTTP/1.1" 500 3313
/home/morty/logs/2019/12/apache_2019-12-30.txt:1.249.123.189 - - [30/12/2019:21:39:36 +0000] "PATCH /alerts HTTP/1.1" 500 4734
/home/morty/logs/2019/12/apache_2019-12-30.txt:124.114.135.105 - - [30/12/2019:21:39:41 +0000] "PATCH /customers HTTP/1.1" 500 3348
/home/morty/logs/2019/12/apache_2019-12-30.txt:35.215.100.202 - - [30/12/2019:21:39:43 +0000] "PUT /alerts HTTP/1.1" 500 4345
/home/morty/logs/2019/12/apache_2019-12-30.txt:86.222.23.128 - - [30/12/2019:21:39:44 +0000] "PATCH /alerts HTTP/1.1" 500 2230
/home/morty/logs/2019/12/apache_2019-12-30.txt:20.161.75.95 - - [30/12/2019:21:39:48 +0000] "DELETE /users HTTP/1.1" 500 2412
/home/morty/logs/2019/12/apache_2019-12-30.txt:196.18.151.117 - - [30/12/2019:21:39:55 +0000] "PUT /events HTTP/1.1" 500 4439
/home/morty/logs/2019/12/apache_2019-12-30.txt:77.101.138.151 - - [30/12/2019:21:39:57 +0000] "PUT /lists HTTP/1.1" 500 2194

## База данных

* Задание 1

У тебя есть база данных с поездками на такси. По плану на линию обслуживания должно было выйти 10550 автомобилей — эта цифра покрывает спрос пользователей. Команде поступило много жалоб: свободных автомобилей оказалось недостаточно. Сколько такси вышло на линии на самом деле? Информация о всех машинах на линии есть в таблице cabs.
Зайди на удалённый сервер.
Подключись к базе данных chicago_taxi, используй логин morty и пароль smith.
Посчитай, сколько всего автомобилей в таблице cabs. Учти, что один автомобиль может принадлежать разным компаниями.

Число автомобилей: 5529

Запрос, которым тебе удалось решить задачу.

\c chicago_taxi

SELECT COUNT(*) AS cnt FROM cabs;

* Задание 2

Посчитай количество автомобилей в каждой компании из таблицы cabs. Отсортируй значения по убыванию. Команда предполагает, что некоторые компании не вывели достаточно автомобилей на линию. 
Выведи те компании, в которых меньше 100 автомобилей. Поле с числом автомобилей назови cnt, поле с названием компании — company_name.
  
Список компаний с числом автомобилей меньше 100.

| cnt |                 company_name |
|:-:|:-:|
  97 | Nova Taxi Affiliation Llc |
  89 | Patriot Taxi Dba Peace Taxi Associat |
  85 | Blue Diamond |
  81 | Checker Taxi Affiliation |
  80 | Chicago Medallion Management |
  69 | Chicago Independents |
  67 | 24 Seven Taxi |
  60 | Checker Taxi |
  55 | American United |
  53 | Chicago Medallion Leasing INC |
  49 | Top Cab Affiliation |
  48 | KOAM Taxi Association |
  38 | Chicago Taxicab |
  34 | Norshore Cab |
  20 | Gold Coast Taxi |
  20 | Metro Group |
  18 | Service Taxi Association |
  14 | 5 Star Taxi |
   8 | American United Taxi Affiliation |
   8 | Metro Jet Taxi A |
   7 | Setare Inc |
   1 | 5997 - 65283 AW Services Inc. |
   1 | 2092 - 61288 Sbeih company |
   1 | 1469 - 64126 Omar Jada |
   1 | 2733 - 74600 Benny Jona |
   1 | 2192 - 73487 Zeymane Corp |
   1 | 5006 - 39261 Salifu Bawa | 
   1 | 3556 - 36214 RC Andrews Cab |
   1 | 3721 - Santamaria Express, Alvaro Santamaria |
   1 | 2809 - 95474 C & D Cab Co Inc. |
   1 | 2241 - 44667 - Felman Corp, Manuel Alonso |
   1 | 3620 - 52292 David K. Cab Corp. |
   1 | 2823 - 73307 Lee Express Inc |
   1 | 6057 - 24657 Richard Addo |
   1 | 6742 - 83735 Tasha ride inc |
   1 | 1085 - 72312 N and W Cab Co |
   1 | 3591 - 63480 Chuks Cab |
   1 | 0118 - 42111 Godfrey S.Awir |
   1 | 6574 - Babylon Express Inc. |
   1 | 3094 - 24059 G.L.B. Cab Co |
   1 | 5874 - 73628 Sergey Cab Corp. |
   1 | 6743 - 78771 Luhak Corp |
   1 | 5074 - 54002 Ahzmi Inc |
   1 | 3623 - 72222 Arrington Enterprises |
   1 | 4053 - 40193 Adwar H. Nikola |
   1 | Chicago Star Taxicab |
   1 | 3011 - 66308 JBL Cab Inc. |
(51 rows) 

Запрос, которым тебе удалось решить задачу.

\c chicago_taxi

SELECT COUNT(cab_id) AS cnt, company_name FROM cabs GROUP BY company_name HAVING COUNT(cab_id) < 100 ORDER BY cnt DESC

* Задание 3

В приложении такси рассчитывается коэффициент стоимости поездки. Если погода хорошая, значение коэффициента равно 1. Если на улице дождь или шторм, коэффициент повышается до 2. У команды есть гипотеза, что в расчётах коэффициента ошибка. Чтобы проверить расчёт коэффициента, команде нужна выборка данных: разработчик может сверить коэффициент с данными в логах и исправить баг. Твоя задача — получить выборку.
Чтобы это сделать:
Получи описание погодных условий из таблицы weather_records для каждого часа.
Раздели все часы на две группы оператором CASE: Bad, если поле description содержит слова rain или storm; Good для всех остальных.
Полученное поле назови weather_conditions.
В результирующей таблице должно быть два поля — дата и час (ts) и weather_conditions.
Сделай выборку за период с 2017-11-05 00:00 по 2017-11-06 00:00.
  
Таблица с данными за указанный период. 

|        ts          | weather_conditions|
|:-:|:-:|
| 2017-11-05 00:00:00 | Good |
| 2017-11-05 01:00:00 | Bad |
| 2017-11-05 02:00:00 | Good |
| 2017-11-05 03:00:00 | Good |
| 2017-11-05 04:00:00 | Bad |
| 2017-11-05 05:00:00 | Bad |
| 2017-11-05 06:00:00 | Good |
| 2017-11-05 07:00:00 | Good |
| 2017-11-05 08:00:00 | Good |
| 2017-11-05 09:00:00 | Good |
| 2017-11-05 10:00:00 | Good |
| 2017-11-05 11:00:00 | Good |
| 2017-11-05 12:00:00 | Good |
| 2017-11-05 13:00:00 | Good |
| 2017-11-05 14:00:00 | Bad |
| 2017-11-05 15:00:00 | Good |
| 2017-11-05 16:00:00 | Bad |
| 2017-11-05 17:00:00 | Good |
| 2017-11-05 18:00:00 | Bad |
| 2017-11-05 19:00:00 | Bad |
| 2017-11-05 20:00:00 | Bad |
| 2017-11-05 21:00:00 | Good |
| 2017-11-05 22:00:00 | Good |
| 2017-11-05 23:00:00 | Good |
| 2017-11-06 00:00:00 | Good |
(25 rows)

Запрос, которым удалось решить задачу.

\c chicago_taxi

SELECT ts, CASE WHEN description LIKE '%rain%’ OR description LIKE '%storm%' THEN ‘Bad’ ELSE ‘Good’ END AS weather_conditions FROM weather_records WHERE ts BETWEEN '2017-11-05 00:00:00' AND '2017-11-06 00:00:00';

* Задание 4

После обновления ПО таксопарки стали сообщать, что прибыль, которую они получают, не сходится с данными, которые отдаёт приложение. Разработка предполагает, что проблема может быть в данных о количестве поездок. 
Чтобы определить, есть ли баг, нужно получить выборку с количеством поездок каждого таксопарка за 15 и 16 ноября 2017 года. 
Выведи поле company_name. Поле с числом поездок назови trips_amount и выведи его.
Результаты, полученные в поле trips_amount, отсортируй по убыванию.
  
Таблица с данными за указанный период.
|                 company_name | trips_amount |
|:-:|:-:|
 Choice Taxi Association                      |         5015 |
 Globe Taxi                                   |         4383 |
 Dispatch Taxi Affiliation                    |         3355 |
 Nova Taxi Affiliation Llc                    |         3175 |
 Patriot Taxi Dba Peace Taxi Associat         |         2235 |
 Checker Taxi Affiliation                     |         2216 |
 Blue Diamond                                 |         2070 |
 Chicago Medallion Management                 |         1955 |
 24 Seven Taxi                                |         1775 |
 Chicago Medallion Leasing INC                |         1607 |
 Checker Taxi                                 |         1486 |
American United                              |         1404 |
 Chicago Independents                         |         1296 |
 KOAM Taxi Association                        |         1259 |
 Chicago Taxicab                              |         1014 |
 Top Cab Affiliation                          |          978 |
 Gold Coast Taxi                              |          428 |
 Service Taxi Association                     |          402 |
 5 Star Taxi                                  |          310 |
 303 Taxi                                     |          250 |
 Setare Inc                                   |          230 |
 American United Taxi Affiliation             |          210 |
 Leonard Cab Co                               |          147 |
 6574 - Babylon Express Inc.                  |           31 |
 Chicago Star Taxicab                         |           29 |
 1085 - 72312 N and W Cab Co                  |           29 |
 2809 - 95474 C & D Cab Co Inc.               |           29 |
 2092 - 61288 Sbeih company                   |           27 |
 3011 - 66308 JBL Cab Inc.                    |           25 |
 3620 - 52292 David K. Cab Corp.              |           21 |
 4615 - 83503 Tyrone Henderson                |           21 |
 3623 - 72222 Arrington Enterprises           |           20 |
 5074 - 54002 Ahzmi Inc                       |           16 |
 2823 - 73307 Lee Express Inc                 |           15 |
 4623 - 27290 Jay Kim                         |           15 |
 3721 - Santamaria Express, Alvaro Santamaria |           14 |
 5006 - 39261 Salifu Bawa                     |           14 |
2192 - 73487 Zeymane Corp                    |           14 |
 6057 - 24657 Richard Addo                    |           13 |
 5997 - 65283 AW Services Inc.                |           12 |
 Metro Group                                  |           11 |
 5062 - 34841 Sam Mestas                      |            8 |
 4053 - 40193 Adwar H. Nikola                 |            7 |
 2733 - 74600 Benny Jona                      |            7 |
 5874 - 73628 Sergey Cab Corp.                |            5 |
 2241 - 44667 - Felman Corp, Manuel Alonso    |            3 |
 3556 - 36214 RC Andrews Cab                  |            2 |
(64 rows)

Запрос, которым удалось решить задачу.

\c chicago_taxi

SELECT cabs.company_name as company_name, count(trips.cab_id) as trips_amount FROM trips INNER JOIN cabs ON cabs.cab_id = trips.cab_id WHERE cast(trips.start_ts as timestamp) >='2017-11-15 00:00:00' AND cast(trips.start_ts as timestamp) < '2017-11-17 00:00:00' GROUP BY company_name ORDER BY trips_amount DESC;
 
