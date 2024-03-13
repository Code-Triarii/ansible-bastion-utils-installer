<div align="center">
<!--
  REMEMBER THAT AT THE END OF THE MARKDOWN PAGES, THERE IS A SECTION WITH ALL THE LINKS TO BE MODIFIED OR ADDED NEW.
  This increases readability.
 -->

<!-- PROJECT LOGO -->

# 📝 Ansible Bastion Utils Installer

<!-- TECNOLOGIES -->

![Ansible Badge](https://img.shields.io/badge/Ansible-E00?logo=ansible&logoColor=fff&style=for-the-badge)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)

This project allows to install some of the most common dependencies in the host machine for server OS.
Starting with Ubuntu 22.04 LTS

</div>

## 📚 Table of contents

- [📝 Ansible Bastion Utils Installer](#-ansible-bastion-utils-installer)
  - [📚 Table of contents](#-table-of-contents)
  - [Structure](#structure)
  - [🚀 Installation and Execution](#-installation-and-execution)
    - [🔨 Prerequisites](#-prerequisites)
    - [🔧 Execution](#-execution)
      - [Local environment](#local-environment)
      - [Docker environment](#docker-environment)
  - [📍 Roadmap](#-roadmap)
  - [📎 Contributing](#-contributing)
  - [📃 License](#-license)
  - [👥 Contact](#-contact)

<!--te-->

## Structure

The repository configuration is simple, it contains the main ansible files:

- `ansible.cfg`
- `playbooks`: contains the different Ansible resources for installation.
  - `dependencies`: this playbooks are configured to be executed for a set of targets.

[🔝 Back to top](#-ansible-bastion-utils-installer)

## 🚀 Installation and Execution

### 🔨 Prerequisites

- For docker execution:
  - `Docker` - Only for the docker execution approach. [Official installation instructions](https://docs.docker.com/engine/install/)
- For local ansible execution:
  - `Python 3.10+`
  - `Ansible`

```bash
# Ubuntu installation
sudo apt-get update && sudo apt-get install -y python3 python3-pip

pip install ansible

# If local installation, include python bins in path
echo 'export PATH=/home/<user>/.local/bin:$PATH' > ${HOME}/.bashrc
```

[🔝 Back to top](#-ansible-bastion-utils-installer)

### 🔧 Execution

#### Local environment

There are several ways to execute it locally, depending on the use case.

1. For localhost with password for sudo (`-K` is short version of `--ask-become-pass`)

```bash
# For localhost
ansible-playbook playbooks/main.yml -i "localhost" -u $(id -un) -K
```

2. In remote machine with private key (assuming `ubuntu` as the remote user. You can change for your matching).

```bash
ansible-playbook playbooks/main.yml -i "<remote-host>" -u ubuntu --private-key priv.key
```

> \[!NOTE\] Do not forget to fetch the `priv.key` and apply `chmod 400 priv.key` or it will raise an error.
> \[!TIP\] You can add the environment variable `ANSIBLE_HOST_KEY_CHECKING=False` before the command execution if you face some issues. However, this is not a good security practice and should be avoided for production usage.

#### Docker environment

1. Build docker image:

```bash
docker build --build-arg UID=$(id -u) --build-arg GID=$(id -g) --build-arg GROUP=$(id -gn) --build-arg USER=$(id -un) \
-t ansible:1.0 .
```

2. Run docker image:

```bash
docker run -it --rm -v $(pwd):/app -w /app ansible:1.0 ansible-playbook playbooks/main.yml -i "<remote-host>" -u ubuntu --private-key priv.key
```

[🔝 Back to top](#-ansible-bastion-utils-installer)

<!-- ROADMAP -->

## 📍 Roadmap

- [x] Add Documentation
- [x] Support automatic installations for Ubuntu family (20.04, 22.04 and 23.10)
- [x] Contenerized execution prepared.

[🔝 Back to top](#-ansible-bastion-utils-installer)

<!-- CONTRIBUTING -->

## 📎 Contributing

Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated** :chart:.

If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply open an issue with the tag "enhancement".

1. Fork the Project
2. Create your Feature Branch
   ```sh
   git checkout -b feature/AmazingFeature
   ```
3. Commit your Changes
   ```sh
   git commit -m 'Add some AmazingFeature
   ```
4. Push to the Branch
   ```sh
   git push origin feature/AmazingFeature
   ```
5. Open a Pull Request

[🔝 Back to top](#-ansible-bastion-utils-installer)

<!-- LICENSE -->

## 📃 License

Distributed under the `Apache 2.0` License. See `LICENSE` for more information.

[🔝 Back to top](#-ansible-bastion-utils-installer)

<!-- CONTACT -->

## 👥 Contact

<div align="center">

[![X](https://img.shields.io/badge/X-%23000000.svg?style=for-the-badge&logo=X&logoColor=white)](https://twitter.com/codetriariism)
[![TikTok](https://img.shields.io/badge/TikTok-%23000000.svg?style=for-the-badge&logo=TikTok&logoColor=white)](https://www.tiktok.com/@codetriariism)
[![Medium](https://img.shields.io/badge/Medium-12100E?style=for-the-badge&logo=medium&logoColor=white)](https://medium.com/@codetriariism)
[![YouTube](https://img.shields.io/badge/YouTube-%23FF0000.svg?style=for-the-badge&logo=YouTube&logoColor=white)](https://www.youtube.com/@CodeTriariiSM)
[![Instagram](https://img.shields.io/badge/Instagram-%23E4405F.svg?style=for-the-badge&logo=Instagram&logoColor=white)](https://www.instagram.com/codetriariismig/)

</div>

As we always state, our main purpose is keep learning, contributing to the community and finding ways to collaborate in interesting initiatives.
Do not hesitate to contact us at `codetriariism@gmail.com`

If you are interested in our content creation, also check our social media accounts. We have all sorts of training resources, blogs, hackathons, write-ups and more!
Do not skip it, you will like it :smirk: :smirk: :smirk: :+1:

Don't forget to give the project a star if you liked it! Thanks again! :star2: :yellow_heart:

[🔝 Back to top](#-ansible-bastion-utils-installer)
