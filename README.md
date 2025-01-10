# elixir-installation
Steps to install/debug elixir on ubuntu using asdf

**Useful links**

https://elixir-lang.org/install.html

https://www.erlang.org/downloads

https://github.com/elixir-lang/elixir/releases

https://github.com/asdf-vm/asdf

https://github.com/asdf-vm/asdf-erlang

**Step 1: Simple default installtion**

`sudo add-apt-repository ppa:rabbitmq/rabbitmq-erlang`

`sudo apt update`

`sudo apt install git elixir erlang -y`

**Step2: Install configure asdf**

`git clone https://github.com/asdf-vm/asdf.git ~/.asdf --branch v0.15.0`

`echo '. $HOME/.asdf/asdf.sh' >> ~/.bashrc`

`echo '. $HOME/.asdf/completions/asdf.bash' >> ~/.bashrc`

`source ~/.bashrc`

**Step3: Add plugins for erlang/exlir using asdf**

`asdf plugin-add erlang https://github.com/asdf-vm/asdf-erlang.git`

`asdf plugin-add elixir https://github.com/asdf-vm/asdf-elixir.git`

**Step 4: Install elixir/erlang**

**4.1 Pre reqs for erlang**
For erlang we need

`sudo apt install curl git build-essential ncurses-dev libssl-dev -y`

You may need following
wkhtmltopdf for pdf reporting, imagemagick for efficeint image storage, postgresql-postgis for postgresql connectivity, inotify-tools for notifications

`sudo apt install -y wkhtmltopdf imagemagick postgis postgresql-postgis inotify-tools -y`

Now to list all available versions

`asdf list-all erlang`

`asdf list-all elixir`

**4.2 Install versions of choice**

`asdf install erlang 21.3.8.24`

`asdf install elixir 1.7.4`

or any others like
asdf install erlang 22.0.7
asdf install elixir 1.9.1-otp-22

**4.3 Make default versions to access anywhere**

`asdf global erlang 21.3.8.24`

`asdf global elixir 1.7.4`

**4.4 Check installtion**

`elixir --version`

done

## Run elixir app

1. `cd /path/to/exlixir-app`
2. `mix deps.clean --all`
3. `mix deps.get`
4. `mix deps.compile`
5. `mix phx.server`

done

## Now to Debug elixir

https://marketplace.visualstudio.com/items?itemName=JakeBecker.elixir-ls
1. Install vscode
3. Install exension ElxirLS (you will need v0.33 for elixir 1.7.4)
4. Open your elixir project
5. in .vscode add launch.json wih following content

{
  "version": "0.2.0",
  "configurations": [
    {
      "type": "mix_task",
      "name": "Debug Phoenix Server",
      "request": "launch",
      "task": "phx.server",
      "projectDir": "${workspaceFolder}",
      "env": {
        "MIX_ENV": "dev"
      },
    }
  ]
}

run with play button
done
