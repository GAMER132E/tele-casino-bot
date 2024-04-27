[<img src="https://img.shields.io/badge/Telegram-%40ClassyCasinoBot-blue">](https://t.me/ClassyCasinoBot) (Ru)

# Telegram Virtual Casino

In October 2020 Telegram team released [yet another update](https://telegram.org/blog/pinned-messages-locations-playlists) 
with slot machine dice. Here it is:

![slot machine dice](repo_images/slot_machine.png)

According to [Dice type documentation](https://core.telegram.org/bots/api#dice) in Bot API, slot machine 
emits values 1 to 64. In [dice_check.py](bot/dice_check.py) file you can find all the logic regarding 
matching dice integer value with visual three-icons representation. There is also a test bot [@ClassyCasinoBot](https://t.me/ClassyCasinoBot) 
in Russian to test how it works.  
Dice are generated on Telegram server-side, you your bot cannot affect the result.

## Technology

* [aiogram](https://github.com/aiogram/aiogram) — asyncio Telegram Bot API framework;
* [redis](https://redis.io) — persistent data storage (persistency enabled separately);
* [cachetools](https://cachetools.readthedocs.io/en/stable) — for anti-flood throttling mechanism;
* [Docker](https://www.docker.com) and [Docker-Compose](https://docs.docker.com/compose) — quickly deploy bot in containers.
* Systemd

## Installation

Copy `env_example` file to `.env` (with leading dot), open and edit it. Create `redis_data` and `redis_config` 
directories, put `redis.conf` file into the latter (there is [example](redis.example.conf) in this repo). 
Create `locales` folder with languages subdirs (e.g. `locales/en`) and put your localization file(s) in those subdirs. 
Check [this directory](bot/locales/example) for samples. Please note that only one language can be active at a time.

Finally, run the bot with `docker-compose up -d` command.

Alternative way: you can use Systemd services, there is also an [example](casino-bot.example.service) available.

## Credits to

* [@SHARK](https://t.me/menasting) for initial inspiration
* [@HVGR](https://t.me/hvgrg) for compact dice combination check (f6f42a841d3c1778f0e32)
