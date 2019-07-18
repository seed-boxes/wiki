# How to install Sonarr

## Prerequisites

Sonarr currently requires mono to be installed.

### Apt method

Use this method to install `mono` using `apt` logged in as root:

```bash
apt install -y apt-transport-https dirmngr gnupg ca-certificates lsb-release
apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 3FA7E0328081BFF6A14DA29AA6A19B38D3D831EF
echo "deb https://download.mono-project.com/repo/$(cat /etc/os-release | sed -rn 's/^ID=(.*)$/\1/p') stable-$(lsb_release -cs) main" | tee /etc/apt/sources.list.d/mono-official-stable.list
apt update
apt upgrade
```

## Apt method

Use this method to install Sonarr:

https://sonarr.tv/#downloads-v3-linux

```bash
apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 2009837CBFFD68F45BC180471F4F90DE2A9B4BF8
echo "deb https://apt.sonarr.tv/$(cat /etc/os-release | sed -rn 's/^ID=(.*)$/\1/p') $(lsb_release -cs) main" | tee /etc/apt/sources.list.d/sonarr.list
apt update
apt install sonarr
```

## Local user

### Download and install Sonarr locally.

```bash
mkdir -p ~/{.sonarr,.config/Sonarr}
wget -qO ~/sonarr.tar.gz "https://services.sonarr.tv/v1/download/phantom-develop/latest?version=3&os=linux"
tar -xvzf ~/sonarr.tar.gz --strip-components=1 -C ~/.sonarr
rm -rf ~/sonarr.tar.gz
```

### Configure Sonarr.

```bash
cat > ~/.config/Sonarr/config.xml <<-CONFIG
<Config>
  <LogLevel>Info</LogLevel>
  <Port>8989</Port>
  <UrlBase></UrlBase>
  <BindAddress>*</BindAddress>
  <SslPort>9898</SslPort>
  <EnableSsl>False</EnableSsl>
  <ApiKey></ApiKey>
  <AuthenticationMethod>Forms</AuthenticationMethod>
  <LaunchBrowser>False</LaunchBrowser>
  <Branch>master</Branch>
  <SslCertHash></SslCertHash>
  <UpdateMechanism>BuiltIn</UpdateMechanism>
  <UpdateAutomatically>True</UpdateAutomatically>
  <AnalyticsEnabled>False</AnalyticsEnabled>
</Config>
CONFIG
```