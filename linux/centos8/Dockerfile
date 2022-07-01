FROM centos:latest
USER root
RUN sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-Linux-*
RUN sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-Linux-*
RUN dnf update -y

# systemctl 설치 및  활성화
RUN dnf -y install httpd; dnf clean all; systemctl enable httpd.service
# NetworkManager 설치 및 활성화
RUN dnf -y install NetworkManager; systemctl start NetworkManager; systemctl enable NetworkManager
# 네트워크 툴 설치
RUN dnf -y install net-tools
# nmtui 설치
RUN dnf -y install NetworkManager-tui
# nslookup 설치
RUN dnf install -y bind-utils
# sudo, wget 설치
RUN dnf install sudo wget -y
# 한글 Language-pack 설치
RUN dnf install glibc-langpack-ko -y
# 파이썬 설치
RUN dnf install python3 -y
# clear 명령어 패키지 설치
RUN dnf install ncurses -y

EXPOSE 80

CMD ["/usr/sbin/init"]