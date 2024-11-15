1. Docker ve Kubernetes Bileşenlerini Kurun
Öncelikle Docker ve Kubernetes paketlerini kurmanız gerekiyor. Docker’ın kurulu olduğunu varsayarak, Kubernetes bileşenlerini kurmaya geçebiliriz.

Docker ve Kubernetes için gerekli depoları ekleyin ve kurulum yapın:

# Docker kurulumu (yapmadıysanız)
sudo yum install -y docker
sudo systemctl start docker
sudo systemctl enable docker

# Kubernetes repo'larını ekleyin
sudo tee /etc/yum.repos.d/kubernetes.repo <<EOF
[kubernetes]
name=Kubernetes
baseurl=https://packages.cloud.google.com/yum/repos/kubernetes-el7-x86_64
enabled=1
gpgcheck=1
repo_gpgcheck=1
gpgkey=https://packages.cloud.google.com/yum/doc/yum-key.gpg
       https://packages.cloud.google.com/yum/doc/rpm-package-key.gpg
EOF

# Kubernetes bileşenlerini yükleyin
sudo yum install -y kubelet kubeadm kubectl


Kubernetes’i kurduktan sonra kubelet'i başlatmanız gerekiyor.

# Kubelet servisini başlatın
sudo systemctl enable --now kubelet
