Делаем переменную окружения
```bash
export SERVICE_LANGUAGE=ru
```

Можно проверить, что она сохранилась, командой printenv

Если до сих пор не установлено, то устанавливаем 
Проверяем, что transifex-client установлен:
```bash
/edx/app/edxapp/venvs/edxapp/bin/pip list | grep transifex-client
```

Если не установлен:

```bash
/edx/app/edxapp/venvs/edxapp/bin/pip install transifex-client
```

Нужно чтобы файл `~/.transifexrc` был настроен (нужно предварительно зарегистрироваться на сайте и вступить в проект edx)

http://docs.transifex.com/client/config/

```bash
cd /edx/app/forum/cs_comments_service
```

Если нужно скачать перевод, то заходим в окружение edxapp и выкачиваем : 
```bash
sudo -H -u edxapp bash
source /edx/app/edxapp/edxapp_env
bundle exec rake i18n:pull
```
Либо, если перевод свой, положить в папку locale файл ru.yml



