FROM amazonlinux:2

RUN yum -y update && \
    yum -y install \
        systemd \
        https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm \
        epel-release \
        http://rpms.famillecollet.com/enterprise/remi-release-7.rpm \
        yum-utils \
        sudo && \

    sed -i -e "s/priority=10/priority=99/g" /etc/yum.repos.d/amzn2-core.repo && \
    useradd docker && \
    echo 'docker ALL=(ALL) NOPASSWD: ALL' | EDITOR='tee -a' visudo