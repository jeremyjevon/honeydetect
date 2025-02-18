# Honeydetect
A simple weekend project that detects honeypots in a very obvious and intrusive manner. It wil connect to your hosts using different credentials/keys each time. If connecting succeeds `depth` amount of times, the system wil flag the host as a honeypot. Currently supporting SSH and TELNET.

<br>

![https://ibb.co/Cntv4hf](https://i.ibb.co/Jzd2859/Screenshot-2020-05-12-at-20-17-33.png)

## Requirements
```
Golang
```
Get it here [https://golang.org/doc/install](https://golang.org/doc/install)

## Installation

On Linux & MacOS

``` bash
sudo apt install golang-go
git clone https://github.com/StefanGrimminck/honeydetect.git
cd honeydetect
go build
go get <repository requirements>
go build
```

Repository Requirements

```
go get github.com/BurntSushi/toml
go get github.com/fatih/color
go get github.com/patrickmn/go-cache
go get golang.org/x/crypto/ssh
```

Edit ```config.toml``` to change honeydetect configurations

Edit ```addresses.txt``` to specify the IP addresses of the target

Run honeydetect with the command ```./honeydetect```

## Usage

Create a `config.toml` file in the root of the honeydetect directory with the following configuration

| input          | type   | description                                       |
|----------------|--------|---------------------------------------------------|
| inputFile      | string | text file with ip addresses                       |
| depth          | int    | amount of maximum test tries                      |
| timeout        | string | session time-out per host with time scale (s/m/h) |
| username       | string | username to check                                 |
| passwordLength | int    | length of passwords used in check                 |

### Example configuration
```toml
# Configuration
inputFile      = "addresses.txt"
depth          = 2
timeout        = "30s"
username       = "root"
passwordLength = 60
```

### Example input file contents
```text
127.0.0.1
192.168.1.42
10.0.10.1
::1
```
