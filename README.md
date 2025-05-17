# DockerInUbuntuWSL
 Install Docker Engine Directly in Ubuntu WSL (Manual Setup)

Step 1: Update Packages
bash
sudo apt update && sudo apt upgrade -y
Step 2: Install Required Dependencies
bash
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common
Step 3: Add Docker’s Official GPG Key
bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
Step 4: Add Docker Repository
bash
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
