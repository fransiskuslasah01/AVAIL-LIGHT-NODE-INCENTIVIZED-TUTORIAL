<p style="font-size:14px" align="right">
<p align="center">
  <img height="auto" height="auto" src="https://github.com/bangpateng/avail-light-node/assets/38981255/2d242104-c837-4417-bfa7-910f613601e3">
</p>


#  AVAIL LIGHT NODE INCENTIVIZED TUTORIAL

##### Dokumentasi
 * [Avail Resmi Websitesi](https://www.availproject.org/)
 * [Avail Resmi Twitter](https://twitter.com/AvailProject)
 * [Avail Resmi Discord](https://discord.gg/kkHAXZCNZa)
 * [Avail Light Node Dokumentasi](https://docs.availproject.org/operate/node/light-client/)
 * [Avail Light Node Form](https://docs.google.com/forms/d/e/1FAIpQLSeL6aXqz6vBbYEgD1cZKaQ4vwbN2o3Rxys-wKTuKySVR-oS8g/viewform)


###  Persyaratan Perangkat Keras Minimum
- Ubuntu 20.04 LTS
- CPU: 2vCPU (1 core)
- Memory: 4 GB
- Storage: 200 - 500 GB


## Update
```
sudo apt update && sudo apt upgrade -y
sudo apt install make clang pkg-config libssl-dev build-essential git screen protobuf-compiler -y
```

### Rust Intsall
```
curl https://sh.rustup.rs -sSf | sh
```
```
source $HOME/.cargo/env
rustup update nightly
rustup target add wasm32-unknown-unknown --toolchain nightly
```
```
screen -S alight
```
### Clone Github
```
git clone https://github.com/availproject/avail-light.git
cd avail-light
git checkout v1.7.3
```
### Cargo Release
```
cargo build --release
```

### Servis Sistem
```
sudo tee /etc/systemd/system/availd.service > /dev/null <<EOF
[Unit] 
Description=Avail Light Client
After=network.target
StartLimitIntervalSec=0
[Service] 
User=root 
ExecStart= /root/avail-light/target/release/avail-light --network goldberg
Restart=always 
RestartSec=120
[Install] 
WantedBy=multi-user.target
EOF
```
### Sistem
```
sudo systemctl daemon-reload
sudo systemctl enable availd.service
sudo systemctl restart availd.service
```
### Check Log
```
journalctl -u availd -fo cat
```
