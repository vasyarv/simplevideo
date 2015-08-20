#Переводы

##Перевод ORA2
Делаем fork https://github.com/edx/edx-ora2  (мой аккаунт vasyarv)

В `openassessment/locale/ru/LC_MESSAGES` кладем файл django.po и djangojs.po

```bash
git clone https://github.com/[account]/edx-ora2
cd edx-ora2/openassessment/locale/
```

Заходим в виртуальное окружение edxapp:
```bash
sudo -H -u edxapp bash
source /edx/app/edxapp/edxapp_env
django-admin.py compilemessages
```
Это должно скомпилить 2 .mo файла

Заливаем эти 2 файла на наш гитхаб

Открываем файл `edx-platform/requirements/edx/github.txt`

Находим строчку (может отличаться, но в ней должно быть вxождение "ora2" )

`-e git+https://github.com/edx/edx-ora2.git@release-2015-07-14T11.10#egg=edx-ora2`

Меняем на 

`-e git+https://github.com/[account]/edx-ora2.git@[hash/release]#egg=edx-ora2`

hash/release - `хеш коммита или название релиза

Далее устанавливаем именно наш ora2:

`sudo /edx/app/edxapp/venvs/edxapp/bin/pip install git+https://github.com/[account]/edx-ora2`


##Перевод форума
Делаем переменную окружения
```bash
export SERVICE_LANGUAGE=ru
```

Можно проверить, что она сохранилась, командой `printenv`

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
