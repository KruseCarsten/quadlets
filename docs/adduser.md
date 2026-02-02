Create a test user

```shell 
sudo useradd test
```

Open a shell for user test

```shell 
sudo machinectl shell --uid=test
```

Optional step: enable lingering to avoid services from being stopped when the user test logs out.

```shell
loginctl enable-linger test
```

Create directories

```shell
mkdir -p ~/.config/systemd/user
mkdir -p ~/.config/containers/systemd
```