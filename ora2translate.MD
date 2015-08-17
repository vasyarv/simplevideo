Делаем fork https://github.com/edx/edx-ora2  (мой аккаунт vasyarv)

В openassessment/locale/ru/LC_MESSAGES кладем файл django.po и djangojs.po

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
Находим строчку (может отличаться, но в ней должно быть влождение "ora2" )
`-e git+https://github.com/edx/edx-ora2.git@release-2015-07-14T11.10#egg=edx-ora2`
Меняем на 
`-e git+https://github.com/[account]/edx-ora2.git@[hash/release]#egg=edx-ora2`
hash/release - `название хеша коммита или релиза

Далее устанавливаем именно наш ora2:
`sudo /edx/app/edxapp/venvs/edxapp/bin/pip install git+https://github.com/[account]/edx-ora2`
