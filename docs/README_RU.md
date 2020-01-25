<p align=center><img src="https://alekslitvinenk.github.io/docker-openvpn/assets/img/logo-s.png"></p>
<br>
<br>

<p align="center">
<a href="https://github.com/alekslitvinenk/docker-openvpn/blob/master/README.md">[English]</a>
<a href="https://github.com/alekslitvinenk/docker-openvpn/blob/master/docs/README_RU.md">[Русский]</a>
<br>

![Build Status](https://cicd.dockovpn.io/build/docker-openvpn)
![Build Time](https://cicd.dockovpn.io/built/docker-openvpn)
[![Docker Pulls](https://img.shields.io/docker/pulls/alekslitvinenk/openvpn.svg)](https://hub.docker.com/r/alekslitvinenk/openvpn/)
[![Gitter chat](https://img.shields.io/badge/chat-on_gitter-50b6bb.svg)](https://gitter.im/docker-openvpn/community)
![GitHub](https://img.shields.io/github/license/alekslitvinenk/docker-openvpn)

# 🔐Docker-Openvpn
Докеризированный OpenVPN cервер, который работает прямо из коробки, не требует долгой настройки и постоянного места на жестком диске. Стартует за 2 секунды. Высокий уровень безопасности.

## GitHub репозиторий:
https://github.com/alekslitvinenk/docker-openvpn

## DockerHub репозиторий:
https://hub.docker.com/r/alekslitvinenk/openvpn

### Докер теги
| Тег    | Описание    | 
| :----: | :---------: |
| `latest` | Этот тег добавляется ко всем новым сборкам docker-openvpn: `v#.#.#` или `v#.#.#-regen-dh` |
| `v#.#.#` | Стандартная фиксированная релиз версия. Здесь {1} указывает на _мажорную версию_, {2} - _минорную_ и {3} - это a _патч_. Пример - `v1.1.0` |
| `v#.#.#-regen-dh` | Релизная версия с обновленным файлом Деффи Хеллмана. Чтобы поддерживать уровень безопасности контейнера на высоком уровне, новая сборка с постфиксом тега `regen-dh` генерируется каждый час. Пример - `v1.1.0-regen-dh` |
| `dev` | Рабочая сборка Dockovpn, которая содержит последние изменения из ветки где ведется активная разработка (master) |

# Видео руководство 📹
<p align=center><a href="https://youtu.be/A8zvrHsT9A0"><img src="https://alekslitvinenk.github.io/docker-openvpn/assets/img/video-cover-play.png"></a></p><br>

# Быстрый старт 🚀

### Предварительные ревизиты:
1. Сервер: физический или виртуальный. У вас должны быть права администратора на данной машине.
2. Докер.
3. Публичный IP адрес.

## 1. Запуск docker-openvpn
Скопируйте код ниже и вставьте его в консоли вашего сервера:<br>
```bash
docker run --cap-add=NET_ADMIN \
-p 1194:1194/tcp -p 80:8080/tcp \
-e HOST_ADDR=$(curl -s https://api.ipify.org) \
alekslitvinenk/openvpn
```

Если все предыдущие шаги были выполнены верно, то мы должны увидеть в консоли нечто похожее:
```
Sun Jun  9 08:56:11 2019 Initialization Sequence Completed
Sun Jun  9 08:56:12 2019 Client.ovpn file has been generated
Sun Jun  9 08:56:12 2019 Config server started, download your client.ovpn config at http://example.com/
Sun Jun  9 08:56:12 2019 NOTE: After you download you client config, http server will be shut down!
 ```

Сервис поднимет одноразовый http-сервер для того чтобы вы могли скчать файл с клиентскими настройками. После того как файл будет скачан, http-сервер будет остановлен.

## 2. Получите клиенсткий файл конфигурации
Теперь, когда сервер запущен, вы можете прейти на `<IP адрес вашего сервера>` в браузере и скачать клиенсткий файл конфигурации. Загрузка фала должна начаться немедленно.<br>
Как только вы загрузите файл, в консоле вашего сервера вы увидите сообщение о том что http сервер был остановлен.

```
Sun Jun  9 09:01:15 2019 Config http server has been shut down
```
Импортируйте `client.ovpn` в ваш любимий клиент OpenVPN. В большинстве случаев достаточно дважды кликнуть на файл чтобы инициировать импорт настроек.

## 3. Подключитесь в вашему контейнеру docker-openvpn
Вы должны увидеть вашу новую конфигурацию в списке доступных конфигураций для подключения. Кликните ее и начнется установка соединения. Через пару секунд все будет готово.

Поздравляем, теперь вы можете безопасно путешествовать по Всемирной Сети!

# Другие русурсы
[Руководство контрибьютора (на английском)](https://github.com/alekslitvinenk/docker-openvpn/blob/master/CONTRIBUTING.md)<br>
[Кодекс поведения (на английском)](https://github.com/alekslitvinenk/docker-openvpn/blob/master/CODE_OF_CONDUCT.md)<br>
[Лицензионное соглашение (на английском)](https://github.com/alekslitvinenk/docker-openvpn/blob/master/LICENSE)
