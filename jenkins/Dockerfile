FROM jenkins/jenkins
USER root
 
# Update
RUN apt-get update -y

# Git
RUN apt-get install -y git

# Terraform
RUN apt-get install -y \
    gnupg \
    software-properties-common

# Ansible
RUN apt-get install -y \
    python3 \
    python3-pip

# Docker
RUN apt-get install -y \
    apt-transport-https \
    ca-certificates \
    curl

# Install Terraform
RUN curl -fsSL https://apt.releases.hashicorp.com/gpg | gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
RUN echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | tee /etc/apt/sources.list.d/hashicorp.list
RUN apt-get update -y && apt-get install -y terraform

# Install Ansible
RUN apt-get update -y && python3 -m pip install ansible --break-system-packages

# Install Docker
RUN mkdir -p /etc/apt/keyrings
RUN  curl -fsSL https://download.docker.com/linux/debian/gpg | gpg --dearmor -o /etc/apt/keyrings/docker.gpg
RUN echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian \
  $(lsb_release -cs) stable" | tee /etc/apt/sources.list.d/docker.list > /dev/null
RUN apt-get update -y && apt-get install -y docker-ce docker-ce-cli containerd.io
RUN usermod -aG docker jenkins

USER jenkins
