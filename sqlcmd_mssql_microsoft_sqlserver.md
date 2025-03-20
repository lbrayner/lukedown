# Ubuntu 24.04

<https://learn.microsoft.com/en-us/sql/tools/sqlcmd/sqlcmd-utility>

Official instructions contain errors. Command `sqlcmd` is provided by the
`mssql-tools18` package.

```bash
curl https://packages.microsoft.com/keys/microsoft.asc | sudo tee /etc/apt/trusted.gpg.d/microsoft.asc
echo 'deb [arch=amd64,arm64,armhf signed-by=/etc/apt/trusted.gpg.d/microsoft.asc] https://packages.microsoft.com/ubuntu/24.04/prod noble main' | sudo tee /etc/apt/sources.list.d/microsoft.ubuntu.list
sudo apt update
sudo apt install mssql-tools18
```

Finally add `/opt/mssql-tools18/bin` to `$PATH`.
