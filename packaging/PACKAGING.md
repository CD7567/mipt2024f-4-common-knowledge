## Как сделать свой пакет общедоступным

### PyPi

[PyPi](https://pypi.org) это открытый репозиторий python пакетов. Через него доступны все пакеты сразу при помощи pip. Пример уже загруженного модуля [тут](https://pypi.org/project/mipt2024f-4-barrect/).

### Guide

Приведем пошаговый путь от кода до деплоя пакета (написано под Linux/MacOS, на Windows можно применять Git Bash или WSL, ну или найти аналоги используемых средств):

1. Подготовить сетап на локальной машине (написано под Linux/MacOS)
    - Установить python-пакет `setuptools`
    - Установить утилиту `twine` (загрузчик в PyPi)
    - Создать в корне своего проекта `python-setup.py` аналогично приложенному
2. Подготовить свой PyPi
    - Завести аккаунт
    - Выпустить API-токен для подгрузки пакетов
3. Собрать пакет локально
```bash
python3 python-setup.py sdist bdist_wheel
```
4. Задеплоить свежесобранный пакет
```bash
twine upload dist/* -u __token__ -p <your token here>
```

Для удобства отдельно приведу single-line команду для итеративного деплоя:
```bash
rm -rf dist && python3 python-setup.py sdist bdist_wheel && twine upload dist/* -u __token__ -p <your token here>
```
