# Ansible Роль: Установка Node Exporter

## Описание
Эта Ansible-роль устанавливает и настраивает Prometheus Node Exporter на целевых серверах.

## Требования
Для использования этой роли необходимо установить её через Ansible Galaxy:

```bash
ansible-galaxy install -p roles -r roles/requirements.yml
```

Файл `roles/requirements.yml` должен содержать:

```yaml
- src: https://github.com/filatof/node-exporter-ansible-role.git
  name: node-exporter
  scm: git
  version: main
```

## Переменные роли
Роль поддерживает следующие переменные, которые можно настроить:

- `node_exporter_version` – версия Node Exporter (по умолчанию: `1.6.1`).
- `node_exporter_user` – системный пользователь для запуска (по умолчанию: `node_exporter`).
- `node_exporter_group` – группа пользователя (по умолчанию: `node_exporter`).
- `node_exporter_web_listen_address` – адрес и порт, на котором будет работать Node Exporter (по умолчанию: `:9100`).
- `node_exporter_bin_path` – путь для установки бинарного файла (по умолчанию: `/usr/local/bin/node_exporter`).

Все переменные можно переопределять в `vars/main.yml`, `defaults/main.yml` или передавать через параметры при вызове роли.

## Зависимости
Роль не имеет внешних зависимостей.

## Пример использования
Пример использования роли в playbook:

```yaml
- hosts: all
  become: yes
  roles:
    - role: node-exporter
      node_exporter_version: "1.6.1"
      node_exporter_web_listen_address: ":9100"
```

## Лицензия
BSD

## Автор
Разработчик: filatof EQ
Репозиторий: [GitHub](https://github.com/filatof/node-exporter-ansible-role)

