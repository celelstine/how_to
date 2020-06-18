## Install Docker in Ubuntu

Reference: https://linuxconfig.org/how-to-install-docker-on-ubuntu-20-04-lts-focal-fossa

Here are the steps:
- Install docker `sudo apt install docker.io`
- Enable docker to start when OS start `sudo systemctl enable --now docker`
- Might want to enable the user to run docker without sudo, `sudo usermod -aG docker ${USER}`
- Try to restart the pc
- Test the installation `docker --version` and `docker run hello-world `
