# Домашнее задание к занятию "08.02 Работа с Playbook"

## Описание Playbook

Данный playbook разворачивает и подготавливает окружение для запуска clickhouse и vector на заданных хостах.

Используемые параметры:

clickhouse_version - версия Clickhouse (в переменной задана 22.3.3.44)
vector_version - версия Vector  (в переменной задана 0.22.3)
clickhouse_packages - имя пакетов Clickhouse

Костыль:
Из-за бардака в репозитории Vector в playbook явно указана -1 в названии файла дистрибутива, т.к в имя rpm пакета добавлена единица.
При изменении версии пакета, следует обратить внимание
Так же там отсутсвуют GPG ключи, и их проверку пришлось отключить

    - block:
        - name: Get Vector distrib
          ansible.builtin.get_url:
            url: "https://packages.timber.io/vector/{{ vector_version }}/vector-{{vector_version}}**-1.**x86_64.rpm"

