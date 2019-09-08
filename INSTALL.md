# Cài đặt môi trường phục vụ lập trình và sử dụng Hyperledger Fabric - NodeJS SDK

## Tùy chọn:
Để cài đặt trên máy ảo và tiện sử dụng thì nên sử dụng SSH
```
sudo apt update
sudo apt install openssh-server -y
sudo systemctl status ssh
ssh username@ip
```

Cài đặt zsh, oh-my-zsh: Yêu cầu máy đã có git
```bash
wget https://gist.githubusercontent.com/pcyan/acf05b05e210df3f56c63044fb8e0e52/raw/5251e32705c0c8cfdf0cecaaac1088654cd0a2e3/auto_config_zsh_tmux_powerline.sh
sudo chmod +x auto_config_zsh_tmux_powerline.sh
sudo .\auto_config_zsh_tmux_powerline.sh
```

Cài đặt auto-suggestion cho zsh:
```bash
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
sudo gedit ~/.zshrc
```

```config
plugins=(git zsh-autosuggestions)
ZSH_AUTOSUGGEST_HIGHLIGHT_STYLE='fg=5'
```
## I. Cài đặt môi trường cho Hyperledger Fabric:
### 1. Các phần mềm cần có trước khi bắt đầu:
- git
```bash
sudo apt-get install git -y
```
- curl
```
sudo apt-get install curl -y
```
- NodeJS  v8.9.0 or higher, up to 9.0 ( Node v9.0+ is not supported for NodeJS SDK )
```

curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -
sudo apt-get update
sudo apt-get install nodejs -y
node --version
npm -v
```
* Cấu hình npm để không cần lệnh sudo
```bash
mkdir ~/.npm
npm config set prefix ~/.npm
sudo nano ~/.zshrc
export PATH="$PATH:$HOME/.npm/bin"
source ~/.zshrc
```
- Docker
```
sudo apt-get update
sudo apt-get remove docker docker-engine docker.io
sudo apt install docker.io
sudo systemctl start docker
sudo systemctl enable docker
sudo usermod -a -G docker $USER
```

- Docker CE
```
sudo curl -L "https://github.com/docker/compose/releases/download/1.24.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```

** Kiểm tra môi trường **
```bash
echo -n 'Node: '
node --version
echo -n 'npm: '
npm --version
echo -n 'Docker: '
docker --version
echo -n 'Docker Compose: '
docker-compose --version
echo -n 'Python: '
python -V
```

1. Cài đặt các thư viện:
Khởi động lại máy sau khi docker rồi mới chạy các lệnh này
```bash
curl -sSL http://bit.ly/2ysbOFE | bash -s
export PATH=<path to download location>/bin:$PATH
```

II. Cài đặt môi trường cho NodeJS SDK:
