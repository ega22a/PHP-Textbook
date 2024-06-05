# Учебник по PHP

Данный учебник предназначен для начинающих программистов, которые хотят изучить язык программирования PHP. В учебнике рассматриваются основные концепции языка PHP, а также примеры кода и задачи для самостоятельного решения. Учебник будет полезен как для студентов, так и для широкого круга лиц, желающих изучить PHP.

Для тех, кто хочет продолжить обучение, в учебнике рассмотренны базовые концепции для работы с фреймворком [Laravel](https://laravel.com) и пакетом для создания back-office веб-приложений [Orchid Software](https://orchid.software).

## Перед началом изучения

Перед началом изучения, необходимо настроить среду разработки, а также рабочее окружение. Для этого необходимо произвести настройку вашей операционной системы, а также установить необходимые программы и пакеты.

Для установки среды разработки PHP, ваши устройства должны поддерживать следующие характеристики:

1. Паравиртуализация в BIOS
2. Актуальные версии ОС (Windows 10, Windows 11, Ubuntu 22.*, Debian и т.п.)

### Настройка операционной системы Windows

**Важно!!!** Настройка Windows возможна только на Windows 10 или Windows 11 с обновлениями не ниже 2021 года.

Для настройки Windows, необходимо установить и настроить WSL2 (Windows subsystem for Linux 2). Следуйте следующим шагам:

1. Открыть терминал от имени администратора;
2. Ввести команду:
    ```shell
    wsl --install
    ```
3. У вас откроется окно установки WSL2, следуйте инструкциям;
4. После установки WSL2, у вас установится Ubuntu 22.04 LTS. Вам будет предложено создать пользователя и пароль. **Пароль необходимо запомнить, так как он потребуется для установки программ!** При вводе пароля, символы не отображаются, но они вводятся;
    ![Пример окна настройки Ubuntu 22.04](./assets/imgs/01.png)

Далее настройки идентичны настройке в [Linux](#настройка-операционной-системы-linux).

### Настройка операционной системы Linux

Настройка пакетов будет происходить через менеджер пакетов `apt`. Для начала установим необходимые пакеты, а именно:

1. PHP 8.* и все необходимые модули;
2. Базы данных MySQL и SQLite 3;
3. Composer;
4. Git;
5. Node.js и npm.

Для установки пакетов, вам необходимо выполнить следующую команду в терминале:

```bash
$ sudo add-apt-repository ppa:ondrej/php && \
  sudo apt update && sudo apt upgrade -y && \
  sudo apt install -y openssl git curl unzip mysql-server sqlite3 php8.3-{common,cli,bcmath,curl,mbstring,mysql,tokenizer,xml,zip,sqlite3} && \
  curl -sS https://getcomposer.org/installer -o /tmp/composer-setup.php && \
  sudo php /tmp/composer-setup.php --install-dir=/usr/local/bin --filename=composer && \
  curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | sudo -E bash - && \
  nvm install 22
```

### Установка среды разработки

Для проведения разработки будет использоваться Visual Studio Code. Для установки, вам необходимо перейти на [официальный сайт](https://code.visualstudio.com) и скачать установщик для вашей ОС.

Для дальнейшей работы с PHP, Laravel, а также проведения тестирования и отладки кода, необходимо установить следующие расширения:

1.  [HTML CSS Support](https://marketplace.visualstudio.com/items?itemName=ecmel.vscode-html-css)
2.  [IntelliCode API Usage Examples](https://marketplace.visualstudio.com/items?itemName=VisualStudioExptTeam.intellicode-api-usage-examples)
3.  [Laravel Artisan](https://marketplace.visualstudio.com/items?itemName=ryannaddy.laravel-artisan)
4.  [Laravel Blade formatter](https://marketplace.visualstudio.com/items?itemName=shufo.vscode-blade-formatter)
5.  [Laravel Blade Snippets](https://marketplace.visualstudio.com/items?itemName=onecentlin.laravel-blade)
6.  [Laravel Blade Spacer](https://marketplace.visualstudio.com/items?itemName=austenc.laravel-blade-spacer)
7.  [Laravel Blade Wrapper](https://marketplace.visualstudio.com/items?itemName=IHunte.laravel-blade-wrapper)
8.  [Laravel Extension Pack](https://marketplace.visualstudio.com/items?itemName=onecentlin.laravel-extension-pack)
9.  [Laravel Extra Intellisense](https://marketplace.visualstudio.com/items?itemName=amiralizadeh9480.laravel-extra-intellisense)
10.  [Laravel goto view](https://marketplace.visualstudio.com/items?itemName=codingyu.laravel-goto-view)
11.  [laravel-goto-components](https://marketplace.visualstudio.com/items?itemName=naoray.laravel-goto-components)
12.  [laravel-jump-controller](https://marketplace.visualstudio.com/items?itemName=pgl.laravel-jump-controller)
13.  [PHP](https://marketplace.visualstudio.com/items?itemName=DEVSENSE.phptools-vscode)
14.  [PHP Debug](https://marketplace.visualstudio.com/items?itemName=xdebug.php-debug)
15.  [PHP Extension Pack](https://marketplace.visualstudio.com/items?itemName=xdebug.php-pack)
16.  [PHP Intelephense](https://marketplace.visualstudio.com/items?itemName=bmewburn.vscode-intelephense-client)
17.  [PHP IntelliSense](https://marketplace.visualstudio.com/items?itemName=zobo.php-intellisense)
18.  [PHP Profiler](https://marketplace.visualstudio.com/items?itemName=DEVSENSE.profiler-php-vscode)

Для более простой установки, вы можете произвести установку через установку пакетного файла. Для этого, [скачайте данный файл](./assets/files/ntcte-extensions-pack-0.0.1.vsix), а потом произведите установку через команду в терминале (Windows или Linux):

```shell
$ code --install-extension <путь к файлу ntcte-extensions-pack-0.0.1.vsix>
```

После выполнения данной команды, все должно быть установлено.

### Настройка базы данных и установка системы управления базами данных

Для настройки базы данных необходимо произвести следующие настройки:

1.Открыть установленную Ubuntu 22.* в режиме терминала;
2. Ввести поочередно следующие команды:
```bash
$ sudo mysql
$ CREATE USER 'student'@'%' IDENTIFIED BY 'student';
$ CREATE DATABASE st;
$ GRANT ALL PRIVILEGES ON st.* TO 'student'@'%';
$ FLUSH PRIVILEGES;
$ exit
```
3. Вышеприведенной командой был создан пользователь БД с логином `student` и паролем `student`; была создана база данных с именем `st`; пользователю `student` были выданы полные права на работу с БД `st`.
4. Установите систему управления базами данных DBeaver. Для этого, перейдите на [официальный сайт](https://dbeaver.io/download) и скачайте установщик для вашей ОС.

### Настройка системы управления версиями Git

Для настройки системы управления версиями Git, вам необходимо произвести следующие настройки:

1. Откройте терминал;
2. Введите следующие команды:
```shell
$ git config --global user.name "Ваше имя"
$ git config --global user.email "Ваша почта"
```

## Содержание

*Тут должно быть содержание...*

## Используемые материалы

1. [PHP: Hypertext Preprocessor](https://www.php.net/)
2. [PHP Manual](https://www.php.net/manual/ru/index.php)
3. [PHP Tutorial](https://www.w3schools.com/php/default.asp)
4. [Laravel](https://laravel.com)
5. [Orchid Software](https://orchid.software)