# Ubuntu Development Environment

## upgrade
```
$ cd
$ sudo apt update
$ apt list --upgradable -a
$ sudo apt upgrade
$ sudo reboot
```

## curl
```
$ curl --version

$ cd
$ sudo apt update
$ sudo apt install curl
$ curl --version
```

## git
```
$ git --version

$ cd
$ sudo apt update
$ sudo apt install git
$ git --version
```

## essential
```
$ make --version
$ gcc --version

$ cd
$ sudo apt update
$ sudo apt install build-essential
$ make --version
$ gcc --version
```

## gcc test
```
$ mkdir ~/Tests
$ mkdir ~/Tests/gcc
$ cd ~/Tests/gcc
$ lsblk
$ cp /media/martin/disk/Linux/Tests/gcc/testprogram.c ./
$ ls
$ gcc testprogram.c -o testprogram
$ ls
$ ./testprogram
```

## direnv
```
$ direnv --version

$ cd
$ sudo apt update
$ sudo apt install direnv
$ echo "$SHELL"
$ cat .bashrc
$ echo 'eval "$(direnv hook bash)"' >> .bashrc
$ cat .bashrc
$ source .bashrc
$ exit
$ direnv --version
```

## java
```
$ java -version

$ cd
$ sudo apt update
$ sudo apt install openjdk-11-jdk openjdk-11-jre
$ java -version
```

## nvm
```
$ nvm --version

$ cd
$ cat .bashrc
$ wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh | bash
$ cat .bashrc
$ source .bashrc
$ exit
$ nvm --version
```

## node
```
$ npm --version
$ node --version

$ nvm ls-remote

$ nvm install v16.10.0
$ nvm which v16.10.0

$ nvm install v14.18.0
$ nvm which v14.18.0

$ nvm ls
$ nvm use v16.10.0
$ nvm current
$ npm --version
$ node --version

$ vi ~/.direnvrc

use_nodejs() {
    NODE_VERSION="$1"

    type nvm >/dev/null 2>&1 || . ~/.nvm/nvm.sh --no-use
    nvm use "$NODE_VERSION"
}
```

## Visual Studio Code
```
$ code --version

$ cd ~/Downloads
$ wget -O ~/Downloads/code.deb https://update.code.visualstudio.com/latest/linux-deb-x64/stable
$ ls
$ sudo apt update
$ sudo apt install ./code.deb
$ code --version
```

## Visual Studio Code extension
```
direnv by g3rry
```

## elm
```
$ elm --version

$ cd ~/Downloads
$ curl -L -o elm.gz https://github.com/elm/compiler/releases/download/0.19.1/binary-for-linux-64-bit.gz
$ ls
$ gunzip elm.gz
$ ls
$ chmod a+x elm
$ sudo mv elm /usr/local/bin/
$ elm --version
$ elm repl
> :exit
$ npm install -g elm-test elm-format
$ npm install -g elm-live
```

## Visual Studio Code extension
```
Elm tooling
```

## elm test
```
$ mkdir ~/Tests/elm
$ cd ~/Tests/elm
$ lsblk
$ cp -r /media/martin/disk/Linux/Tests/elm/buttons ./
$ ls
$ cd buttons
$ echo 'use nodejs v14.18.0' >> .envrc
$ cat .envrc
$ direnv allow
$ cd ..
$ cd buttons
$ node --version
$ elm make src/Main.elm --optimize --output=static/main.js
$ elm reactor

http://localhost:8000
```

## kerl
```
$ kerl version

$ cd ~/Downloads
$ curl -O https://raw.githubusercontent.com/kerl/kerl/master/kerl
$ ls
$ chmod a+x kerl
$ sudo mv kerl /usr/local/bin/
$ kerl version
```

## erlang
```
$ erl -version

$ cd
$ sudo apt update
$ sudo apt install libssl-dev
$ sudo apt install automake
$ sudo apt install autoconf
$ sudo apt install m4
$ sudo apt install libncurses5-dev
$ sudo apt install libwxgtk3.0-gtk3-dev
$ sudo apt install libwxgtk-webview3.0-gtk3-dev
$ sudo apt install unixodbc-dev
$ sudo apt install xsltproc
$ sudo apt install fop
$ sudo apt install libxml2-utils

$ kerl update releases
$ kerl list releases

$ kerl build 24.1 24.1
$ kerl install 24.1 ~/erlang/24.1
$ kerl path 24.1

$ kerl build 23.3.4.7 23.3.4.7
$ kerl install 23.3.4.7 ~/erlang/23.3.4.7
$ kerl path 23.3.4.7

$ kerl list builds
$ kerl list installations
$ . ~/erlang/24.1/activate
$ kerl active
$ kerl status
$ erl -version
$ erl
1> halt().

$ vi ~/.direnvrc

use_erlang() {
    ERLANG_VERSION="$1"

    . ~/erlang/$ERLANG_VERSION/activate
}
```

## rebar3
```
$ rebar3 --version

$ mkdir ~/rebar3

$ cd ~/rebar3
$ wget https://github.com/erlang/rebar3/archive/refs/tags/3.17.0.tar.gz -O -| tar xzvf -
$ ls
$ cd rebar3-3.17.0
$ echo 'use erlang 24.1' >> .envrc
$ cat .envrc
$ direnv allow
$ cd ..
$ cd rebar3-3.17.0
$ erl -version

$ ./bootstrap
$ ls
$ ./rebar3 local install
$ ./rebar3 --version

$ ls ~/.cache/rebar3
$ mv ~/.cache/rebar3 ~/.cache/rebar3-3.17.0


$ cd ~/rebar3
$ wget https://github.com/erlang/rebar3/archive/refs/tags/3.15.2.tar.gz -O -| tar xzvf -
$ ls
$ cd rebar3-3.15.2
$ echo 'use erlang 23.3.4.7' >> .envrc
$ cat .envrc
$ direnv allow
$ cd ..
$ cd rebar3-3.15.2
$ erl -version

$ ./bootstrap
$ ls
$ ./rebar3 local install
$ ./rebar3 --version

$ ls ~/.cache/rebar3
$ mv ~/.cache/rebar3 ~/.cache/rebar3-3.15.2
```

## Visual Studio Code extensions
```
erlang-ls
```

## erlang test
```
$ mkdir ~/Tests/erlang
$ cd ~/Tests/erlang
$ lsblk
$ cp -r /media/martin/disk/Linux/Tests/erlang/hello_world ./
$ ls
$ cd hello_world
$ echo 'use erlang 24.1' >> .envrc
$ echo 'PATH_add ~/.cache/rebar3/bin' >> .envrc
$ cat .envrc
$ direnv allow
$ cd ..
$ cd hello_world

$ sudo cp /media/martin/disk/Linux/bash/use-rebar3 /usr/local/bin/
$ sudo chmod a+x /usr/local/bin/use-rebar3

$ use-rebar3 3.17.0
$ use-rebar3

$ rebar3 --version
$ rebar3 shell

http://localhost:8080

1> halt().
```

## postgresql
```
$ systemctl status postgresql

$ cd
$ sudo apt update
$ sudo apt install postgresql-12 postgresql-client-12
$ systemctl status postgresql
$ systemctl status postgresql@12
$ systemctl is-enabled postgresql

$ sudo su postgres
$ ls /etc/postgresql/12/main
$ vi /etc/postgresql/12/main/pg_hba.conf

# TYPE  DATABASE        USER            ADDRESS                 METHOD

# "local" is for Unix domain socket connections only
local   all             all                                     trust
# IPv4 local connections:
host    all             all             127.0.0.1/32            trust
host    all             all             127.0.0.1/32            md5
# IPv6 local connections:
host    all             all             ::1/128                 trust
host    all             all             ::1/128                 md5
# Allow replication connections from localhost, by a user with the
# replication privilege.
local   replication     all                                     trust
host    replication     all             127.0.0.1/32            trust
host    replication     all             ::1/128                 trust


$ vi /etc/postgresql/12/main/postgresql.conf

listen_addresses = '*'


$ systemctl restart postgresql
$ systemctl status postgresql
$ exit

$ psql -h localhost -p 5432 -U postgres
# \q
```

## sqitch
```
$ sqitch --version

$ cd
$ sudo apt update
$ sudo apt install sqitch libdbd-pg-perl
$ sqitch --version
```

## dbeaver
```
$ cd ~/Downloads
$ wget -O - https://dbeaver.io/debs/dbeaver.gpg.key | sudo apt-key add -
$ echo "deb https://dbeaver.io/debs/dbeaver-ce /" | sudo tee /etc/apt/sources.list.d/dbeaver.list
$ sudo apt update
$ sudo apt install dbeaver-ce
```

## slack
```
$ cd ~/Downloads
$ ls
$ sudo apt update
$ sudo apt install ./slack-desktop-4.20.0-amd64.deb
```

## thunderbird
```
$ thunderbird --version

$ cd
$ sudo apt update
$ sudo apt install thunderbird
$ thunderbird --version
```

## libreoffice
```
$ libreoffice --version

$ cd
$ sudo apt update
$ sudo apt install libreoffice
$ libreoffice --version
```

## foliate
```
$ cd ~/Downloads
$ wget https://github.com/johnfactotum/foliate/releases/download/2.6.3/com.github.johnfactotum.foliate_2.6.3_all.deb
$ ls
$ sudo apt update
$ sudo apt install ./com.github.johnfactotum.foliate_2.6.3_all.deb
```
