# DockerInUbuntuWSL

I have encountered the following error when executing terraform apply
```bash
│ Error: Error pinging Docker server: Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running?
│
│   with provider["registry.terraform.io/kreuzwerker/docker"],
│   on main.tf line 10, in provider "docker":
│   10: provider "docker" {}
│
╵
```

Apparently docker were not installed yet in my ubuntu WSL. 

Install Docker Engine Directly in Ubuntu WSL (Manual Setup)

Step 1: Update Packages
```bash
bash
sudo apt update && sudo apt upgrade -y
```

Step 2: Install Required Dependencies
```bash
bash
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common
```

Step 3: Add Docker’s Official GPG Key
```bash
bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

Step 4: Add Docker Repository
```bash
bash
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

Step 5: Install Docker Engine
```bash
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io
```

Step 6: Start Docker Service
```bash
sudo service docker start
```

Step 7: Test Docker
```bash
sudo docker run hello-world
```
If successful, you'll see the "Hello from Docker!" message.


Step 8: Avoid sudo for Docker (Optional)
```bash
sudo usermod -aG docker $USER
```
Restart WSL (wsl --shutdown in PowerShell, then reopen Ubuntu).


Step 9: Verify Docker in WSL
Open Ubuntu WSL and run:

```bash
docker --version
```
Expected output: Docker version 24.0.7, build afdd53b

Step 10: Test if Docker works:

```bash
docker run hello-world
```
If successful, you'll see a "Hello from Docker!" message.



