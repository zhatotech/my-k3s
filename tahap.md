senjata yang saya gunakan :
- Proxmox
  - VM Ubuntu x 3
    NAME="Ubuntu"
    VERSION="20.04.4 LTS (Focal Fossa)"
    ID=ubuntu
    ID_LIKE=debian
    PRETTY_NAME="Ubuntu 20.04.4 LTS"
    VERSION_ID="20.04"
    HOME_URL="https://www.ubuntu.com/"
    SUPPORT_URL="https://help.ubuntu.com/"
    BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
    PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
    VERSION_CODENAME=focal
    UBUNTU_CODENAME=focal

- Update dan Upgrade
```bash
sudo apt update && sudo apt upgrade - y
```

- Deploy K3S
```bash
curl -sfL https://get.k3s.io | sh -
```

- ubah permission agar command bisa dijalankan tanpa sudo
```bash
sudo chmod 644 /etc/rancher/k3s/k3s.yaml
```
sampai disini, instalasi untuk Node Master selesai. Untuk menambahkan worker ikuti langkah berikut:

- copy node-token pada master node
```bash
sudo cat /var/lib/rancher/k3s/server/node-token
```
- masuk ke worker dan lakukan
```bash
export K3S_TOKEN=token_dari_node_master
export K3S_URL=https://ip_address_node_master:6443
```
- Deploy K3S
```bash
curl -sfL https://get.k3s.io | sh -
```
- cek semua node pada master node
```bash
kubectl get nodes
```




