FROM ubuntu:focal

RUN apt update && apt install -y openssh-server sudo vim ufw && \
    mkdir /var/run/sshd && echo "root:root" | chpasswd && \
    sed -ri 's/^#?PermitEmptyPasswords\s+.*/PermitEmptyPasswords yes/' /etc/ssh/sshd_config && \
    sed -ri 's/^#?PermitRootLogin\s+.*/PermitRootLogin yes/' /etc/ssh/sshd_config

# 後でマージ予定のものはここへ
# RUN apt install

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]