# Install Instructions

1. Enable Virutalization:
  - Raspbian: `sudo cp /boot/cmdline.txt /boot/cmdline.txt.bak1
              orig="$(head -n1 /boot/cmdline.txt) cgroup_enable=cpuset cgroup_memory=1 cgroup_enable=memory"
              echo $orig | sudo tee /boot/cmdline.txt
              sudo reboot`
  - Ubuntu: `sudo cp /boot/firmware/cmdline.txt /boot/firmware/cmdline.txt.bak1
              orig="$(head -n1 /boot/firmware/cmdline.txt) cgroup_enable=cpuset cgroup_memory=1 cgroup_enable=memory"
              echo $orig | sudo tee /boot/firmware/cmdline.txt
              sudo reboot`

2. Install k3s: `curl -sfL https://get.k3s.io | sh -`
3. Check master node is running: `sudo k3s kubectl get node`
4. Copy baseconfig to kuberconfig in HD: `sudo cp /etc/rancher/k3s/k3s.yaml ~/kubeconfig`
  - **Change IP to master**
5. Change Owner and Group to Current User: `sudo chown $(whoami):$(whoami) ~/kubeconfig`
6. Use SCP to save the kubeconfig to local machine: `scp username@pi-ip:~/kubeconfig ~/kubeconfig`
7. Export the variable to your rc: `export KUBECONFIG=~/kubeconfig`
8. Check local machine configuration: `kubectl get node`
9. Get master node token: `sudo cat /var/lib/rancher/k3s/server/node-token`


