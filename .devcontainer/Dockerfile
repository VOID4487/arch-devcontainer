# ./Dockerfile
FROM archlinux:latest

# Base tools
RUN pacman -Sy --noconfirm base-devel openssh sudo curl git && pacman -Scc --noconfirm

# Enable SSH
RUN mkdir -p /run/sshd && \
    ssh-keygen -A && \
    echo "PermitRootLogin yes" >> /etc/ssh/sshd_config && \
    echo "PasswordAuthentication yes" >> /etc/ssh/sshd_config

# Optional: non-root user
RUN useradd -m dev && echo "dev:dev" | chpasswd && echo "dev ALL=(ALL) NOPASSWD:ALL" > /etc/sudoers.d/dev

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
