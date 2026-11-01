# minecraft-stress-test

> **Разработка закрыта.**

Форк [PureGero/minecraft-stress-test](https://github.com/PureGero/minecraft-stress-test): консольная утилита, которая заводит на сервер ботов в offline-mode, и те летают по миру и прогружают чанки. Предназначена для нагрузочного тестирования сервера и запускается отдельно от него.

## Что внутри

- Java 17, Maven, Netty 4.1. Боты сами реализуют протокол Minecraft 1.20.6 (по README upstream).
- Параметры задаются через `-Dbot.count`, `-Dbot.ip`, `-Dbot.port`, `-Dbot.login.delay.ms`, `-Dbot.radius`, во время работы ботами управляют командами в консоли (`count`, `speed`, `radius`). Подробности в оригинальном README ниже.

## Сборка

```
mvn
```

Артефакт: `target/minecraft-stress-test-1.0.0-SNAPSHOT-jar-with-dependencies.jar`. На целевом сервере нужны `online-mode=false` и `allow-flight=true`.

## Зависимости

- `io.netty:netty-all` 4.1.73.Final.

## Что изменено относительно оригинала

Оригинал: [PureGero/minecraft-stress-test](https://github.com/PureGero/minecraft-stress-test).

Своих изменений нет, это копия оригинала на коммите `fb03aa8` (02.05.2024, поддержка 1.20.6). Форк отстаёт от upstream на 13 коммитов и не опережает его ни на один.

## Оригинальный README

# minecraft-stress-test

Automate the stress testing of your 1.20.6 Minecraft server with bots.
This project will log offline-mode bots into the specified server which will
fly around and explore the world.

## Building

Download the source code with

```shell
git clone https://github.com/PureGero/minecraft-stress-test.git
```

Build the source code with

```shell
mvn
```

## Running

Ensure the following values are set in your server.properties:

```properties
online-mode=false
allow-flight=true
```

Run the bot with

```shell
java -jar target/minecraft-stress-test-1.0.0-SNAPSHOT-jar-with-dependencies.jar
```

Or, specify optional parameters:

```shell
java
    -Dbot.count=1
    -Dbot.ip=127.0.0.1
    -Dbot.port=25565
    -Dbot.login.delay.ms=100
    -Dbot.radius=1000
    -jar target/minecraft-stress-test-1.0.0-SNAPSHOT-jar-with-dependencies.jar
```

Note that bots are unable to respawn, we recommend giving them creative mode.

### Commmands

You can type some commands into the console to control the bots on the fly.

`count 1000`  
Set the bot count to 1000. This will either connect more bots, or disconnect existing bots as needed.

`speed 0.2`  
Set the bots' movement speed. The default is 0.1 blocks/tick.

`radius 600`  
Set the radius of the area the bots can move around in. The default is 1000 blocks.
