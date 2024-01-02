FROM jenkins/inbound-agent:3192.v713e3b_039fb_e-5

USER root

# Install Openstack Client
RUN apt update && \
    apt install -y python3-dev python3-pip
RUN pip3 install --break-system-packages --upgrade pip
RUN pip3 install --break-system-packages python-openstackclient

# Install Packer
RUN apt update && apt upgrade -y && apt install -y wget gpg lsb-release

RUN wget -O- https://apt.releases.hashicorp.com/gpg | gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg && \
    echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | tee /etc/apt/sources.list.d/hashicorp.list && \
    apt update && apt install -y packer